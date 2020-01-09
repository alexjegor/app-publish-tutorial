# App Signing

Apple Developer Program membership is required to request, download, and use signing certificates issued by Apple. For developers part of a team enrolled as an organization, you must also be the account holder or an admin to request distribution certificates used for submitting apps to the App Store.

> Please visit [this](https://developer.apple.com/account/) link to manage your development account.

<em>NOTE: To develop iOS apps using the latest technologies, you need a Mac computer (macOS 10.11.5 or later) running the latest version of Xcode.</em>

## Prerequisites

During the course of developing your app, you have to create different assets:

1. Certificates
2. App ID
3. Mobile Provision Files

### Certificates

You’ll use `development` certificate to run your app on devices and use app capabilities, and `distribution` certificate to distribute your app for testing and to upload it to App Store Connect.

To create one please visit "Certificates, Identifiers & Profiles" [section](https://developer.apple.com/account/resources/certificates/add) in your developer account, and follow the instructions there. In a nutshell you'll have to create a Certificate Signing Request (CSR) file using Keychain Access application on your Mac and exchange it to .cer file using Apple Certificate Authority. [Learn more](https://help.apple.com/developer-account/#/devbfa00fef7).

Double-click generated .cer file to install Certificate into your login keychain.

> This process is all the same both for Development and Distribution certificate types.

<em>NOTE: If you are going to build your app for Ad Hoc or App Store Distribution on multiple computers, you'll need to export and import your Distribution Certificate into the relevant keychain on each of this computers.</em>

### App ID
An App ID is a two-part string used to identify one or more apps from a single development team. It is a two-part string used to identify one or more apps from a single development team. [Learn more](https://help.apple.com/developer-account/#/dev1b35d6f83).

### Provisioning
As we know, Apple likes to keep things secure, so it is not possible to install an App on any iOS Device out there using only the certificate. This is where Provisioning Profiles comes in. A Provisioning Profile must be installed on each device your application code should run on. Each Development Provisioning Profile will contain a set of iPhone Development Certificates, Unique Device Identifiers and an App ID.

Devices specified in the Development Provisioning Profile can be used for testing only by those individuals whose Development Certificates are included in the profile. A single device can contain multiple provisioning profiles. The difference between Development and Distribution Profiles is that Distribution Profiles don’t specify any Device IDs. If you want to release an App which should be limited to a number of registered devices, you need to use an Ad-Hoc profile for that.

Devices you use for development need to be registered and added to the provisioning profile [here](https://developer.apple.com/account/resources/devices/list).

For more information on how to create, download, edit and delete mobile provision files please visit [this](https://help.apple.com/developer-account/#/devf2eb157f8) link. 

To install it just double click on downloaded `*.mobileprovision` file so it will appear in Xcode

> We would pesonally recommend to create single provision for debug and another one for distribution, as well as certificates

## Automatic Signing

Automatic signing is a target setting that allows Xcode to manage signing assets for you. The signing settings are located in the General pane under the heading Signing in the project editor. To enable automatic signing, select "Automatically manage signing."

If you enable automatic signing, Xcode does the following for you when needed:

* Creates your signing certificates
* Registers connected devices
* Creates and edits App IDs
* Manages provisioning profiles
* Edits the entitlements and information property list files

> To use automatic signing add your Apple ID to Accounts preferences. This will identify you and download information about your teams, add your Apple ID account to Accounts preferences. Xcode uses the Apple ID credentials to download information about all the teams you belong to. <br/>
To open Accounts preferences, choose Xcode > Preferences and click Accounts.

## Automatic vs. Manual

### Pros

* No need to manually generate Provisioning profiles and log into a remote machine each time to copy them over. It is done automatically out-of-box for each new (and existing) project.
* No need to add 3rd party dependencies to the project to enable signing process automation, because each new dependency comes with possible risk.
* With the `Automatically manage signing` feature enabled, it is much easier for a new developer to join the team.

### Cons

* If your project has some specific configuration, for example, custom entitlements, Xcode can forbid you to build your project if you use `Automatically manage signing` feature, because of its inner rules.
* Your remote CI build machine must have a logged in Apple Developer account in Xcode to use `Automatically manage signing` feature. Therefore, you need to keep in mind that everyone who has access to that build machine will have access to that account, too. So it is recommended that you do not use your master account with full access rights for every team certificate.
* If you have a wildcard bundle identifier registered inside your App IDs list, Xcode can automatically select that Application ID and use provisioning profiles generated for it – that way it can cause complications for your build process because this App ID is most likely used in other projects too and can have some negative effects. The recommendation is to avoid wildcard application definitions, or at least add an additional domain name for the wildcard, like, com.example.test.*, not just define *