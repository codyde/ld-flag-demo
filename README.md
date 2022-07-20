# LaunchDarkly Flag Demo Application 

This appalication is designed to use several feature flags to showcase the ability to release features in a variety of ways. 

## Running this application 

This application can be deployed to many different providers, in order for it to run successfully you'll need to leverage an environment variable named `VITE_LD_CLIENT_ID` with the **Client Side SDK** key from LaunchDarkly 

For example - 

```bash
export VITE_LD_CLIENT_ID=<your client ID>
```

### Editing and building in Replit

Using [Replit](https://www.replit.com) you can find a repl of this application under [@launchdarkly/LaunchDarkly Feature Flag Demo](https://replit.com/@LaunchDarkly/LaunchDarkly-Feature-Flag-Demo?v=1). Select `Fork Template` to run your own repl. 

In Replit, you'll need to create a secret that uses the above environment variable to start your repl with the correct information. 

## Feature Flags 

This application uses several feature flags to show LaunchDarkly functionality 

* `qrCode` - This feature flag controls the presence of the QR code in the application. You can modify the URL that returns in this by modifying the variable on Line 3 of `/src/components/qrCode.js`
* `prodHeader` - This feature flag controls the shifting from the introduction of the application, to the updated header with the login URL. This is a standard release of a new feature 
* `upperimage` - This feature displays the image at the top of the page, in the talk track, we build a **individual target** pointed at the specific user who logs on the lefthand side of the page 
* `logoversion` - This feature swaps the Osmo image for toggle. We can use this with either device or browser type targeting rules, or perform a progressive rollout to show 50/50 splits (or other percentages) of the old and new version 
* `cardshow`- This controls the rollout of new feature cards demonstrating "Release" on the bottom of the page

## Building the Feature Flag 

In the `/terraform` directoy you'll find a `main.tf` file that contains a manifest for instantiating all the feature flags. Ensure you are updating the project name within this `main.tf` file with your own project. 

Execute the following commands: 

```bash
terraform init 
terraform apply 
```

You'll be prompted for a LaunchDarkly API key which you can obtain via [LaunchDarkly](https://app.launchdarkly.com)