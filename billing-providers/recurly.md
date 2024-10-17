# Connecting FirstPromoter with Recurly

FirstPromoter allows you to seamlessly track sales, refunds, upgrades and cancellations from Recurly.

## Setting Up

To get started, please follow the below steps:

### Step 1: Set API credentials

1. Open a new browser tab, log in to your Recurly dashboard.
2. On your Recurly dashboard in the left sidebar, select Integrations > API Credentials.
3. Click on Add Private API Key
4. Add a key name such as 'FirstPromoter' and check the 'Read-only' checkbox.
5. Click `Save changes`.
6. Copy the Private API key and paste it into the "Private API key" field in the FirstPromoter Recurly Setup.
7. Provide your Recurly subdomain in the 'Subdomain' field (you can find this in the URL bar, for example, if your URL is `https://mycompany.recurly.com`, your subdomain is 'mycompany').

### Step 2: Set Webhooks

1. On your left sidebar select Integrations > Webhooks.
2. Click on Manage Endpoints.
3. Click on "New Endpoint".
4. Set the Endpoint Name as `FirstPromoter`.
5. Copy the Webhook Endpoint URL from the setup form here and paste it into the Endpoint URL field on Recurly.
6. Leave the format as XML.
7. Scroll down to the notifications section and enable the following events `closed_invoice`, `paid_charge_invoice`, `canceled_subscription`, `void_payment`, `successful_refund`.
8. Click "Save Changes".
