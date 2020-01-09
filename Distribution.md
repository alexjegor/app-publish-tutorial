# App Store Connect

[App Store Connect](https://appstoreconnect.apple.com) is a suite of web-based tools for managing apps sold on the App Store for iPhone, iPad, Mac, Apple Watch, Apple TV, and iMessage. As a member of the Apple Developer Program, you’ll use App Store Connect to submit and manage apps, invite users to test with TestFlight, add tax and banking information, access sales reports, and more.

## Adding Your App’s Information and Metadata
Before you can upload a build of your app to App Store Connect, you must first create it in your App Store Connect account.

To do this, follow this steps:
1. Start in your browser, navigate to [App Store Connect](https://appstoreconnect.apple.com)
2. Log in
3. Open My Apps section
4. Click the plus sign in the top left of the screen to create "New iOS App"
5. Bundle ID: choose the one created on Developer Portal
6. For convenience, make the SKU match the Bundle ID created earlier
7. Click Create to create the first version listing

To get started in distributing your app on the App Store, add your app's information, such as pricing details, descriptions, keywords, screenshots, and more, in App Store Connect. You can do this even before you’re done developing your app.

Here the list of required data:

| Requirements          | Notes |
| --------------------- | ----- |
| Screenshots           | You need at least one for every supported device screen size.  The screenshots cannot contain transparency |
| Name                  | Name of the app as seen by users |
| Description           | A description of your app, detailing features and functionality |
| Keywords              | Separate keywords with a comma |
| Support URL           | A URL with support information for your app |
| App Icon              | This icon will be used on the App Store and must be in the JPG or PNG format, with a minimum resolution of at least 72 DPI, and in the RGB color space. It must not contain layers or rounded corners. |
| Categories            | One of the suggested categories |
| Rating                | Generate your rating based on the questionnaire |
| Copyright             | Use the format: YYYY Company Name |
| Demo Account          | The username and password for a full-access account for your app. Include details for additional accounts in the Notes field |

## Uploading Your App
Once your app details have been entered in App Store Connect, you can upload a build using Xcode or Application Loader. 

Open your project in Xcode, make sure you have a correct Bundle Identifier, and that your Team ID and Release Code Signing Identity are properly set. Choose `Generic iOS Device` in the scheme chooser, then choose `Product > Archive`. If everything is okay with the build, Xcode will open the Organizer window with your app in the Archives tab. Click `Upload to App Store`.
Xcode then prompts you with App Store distribution options. Xcode selects all the check boxes by default, let them go by clicking **Next**
Organizer could also ask you for distribution signing options. You can select automatic signing, or manually select your distribution certificate and provisioning profile. Select the relevant ones, and click **Next** once again.

Once Xcode finishes doing some of its magic, it presents a summary page for the app you’re about to submit. Click **Upload**.

All uploads display on the Activity section of My Apps in App Store Connect, and can be selected for distribution through TestFlight or on the App Store.

That’s all the work required for Xcode. Your beta build is now available on iTunes Connect, and that’s where you’ll be doing the rest of the work.

## TestFlight
Before releasing your app on the App Store, use TestFlight to distribute your beta apps and app updates to testers for valuable feedback. 

Apple defines two types of testers for TestFlight:
* **Internal Tester**: This is an iTunes Connect user that has an Admin, App Manager, Legal, Developer, or Marketer role with access to your app. This is usually a team member or a client for whom you’re developing an app. You can add up to 25 internal testers.
* **External Tester**: This is any user outside of your team that wants to test your app. An external tester has no access to your iTunes Connect account in any way, and can only download and install the app. You can add up to 10,000 external testers.

To start beta testing of your app, go to the My Apps section on the App Store Connect home page and click on your app. Activity tab is the section where you’ll find all the builds you uploaded earlier.

In the left side menu of TestFlight tab you can see `TESTERS & GROUPS` panel. This is the place where you can manage who has beta access to your application.

Before your external testers can test your app, you must submit your TestFlight build to Apple for review, exactly as you would with a normal App Store submission. These reviews tend to go faster than normal app reviews, although you shouldn’t count on it, and once it’s approved, you can let external testers test your app.
Internal testers, on the other hand, are instantaneously notified about new builds as soon as they are uploaded and processed within iTunes Connect. To manage internal testers visit [Users and Access](https://appstoreconnect.apple.com/access/users) section inside App Store Connect

