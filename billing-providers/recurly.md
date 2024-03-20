# Connecting FirstPromoter with Recurly

FirstPromoter allows you to seamlessly track sales, refunds, upgrades, and cancellations from Recurly.

## Setting Up

To get started, please follow the below steps:

### Step 1: Set API credentials

1. Open a new browser tab, log in to your Recurly dashboard, then navigate to Developers > API credentials.
2. Click on "Add Private API key".
3. Add a key name such as 'FirstPromoter' and check the 'Read-only' checkbox.
4. Click 'Save changes'.
5. Copy the Private API key and paste it into the "Private API key" field in the FirstPromoter Recurly Setup.
6. Provide your Recurly subdomain in the 'Subdomain' field (you can find this in the URL bar, for example, if your URL is `https://mycompany.recurly.com`, your subdomain is 'mycompany').

### Step 2: Set Webhooks

1. Return to the Recurly dashboard, go to Developers > Webhooks, and click on the Configure button
2. Click on "New Endpoint".
3. Copy the Webhook Endpoint URL from the setup form here on yor right, and paste it into the Endpoint URL field on Recurly.
4. Click "Save Changes" after you fill the Endpoint Name field

***Please make sure to select "successful payment", "successful refund", "void payment", and "cancelled subscription" events***
