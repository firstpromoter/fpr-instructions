# Connecting FirstPromoter with Braintree

FirstPromoter allows you to seamlessly track sales, upgrades, and cancellations from Braintree.

***Important Note: Due to limitations with Braintree Webhooks, FirstPromoter is unable to automatically handle refunds. All other functions are operational. In the event of a refund, you will need to "Deny" the commission/reward of the affiliate.***

## Setting Up

To get started, please follow the steps below:

### Step 1: Create a Read-Only User Role (optional)

For added security, consider creating a new User Role in Braintree that allows only read operations. If this is not a concern or if you are in the Braintree Sandbox environment, you can proceed to Step 2.

1. Log in as admin to your Braintree account and go to Settings > User and Roles > Manage Roles > New.
2. Provide a role name such as "Read-Only"
3. Uncheck all permissions except for: **Download Transactions with Masked Payment Data**, **Download Vault Records with Masked Payment Data**, **Download Subscription Records, Manage Webhooks**.
4. Click on "Create Role"
5. Now go to Settings > Users and Roles > New user. Grant API Access to the user, assign the read-only role, and assign access to the merchant accounts.
6. Log out of Braintree and log back in as the new 'read-only' user.

### Step 2: Create a new API key

1. Login to Braintree, navigate to Account > My User (on the top menu) and scroll down until you see: API keys, Tokenization Keys, Encryption keys.
2. Click on View Authorizations under it.
3. In the API keys section, click "Generate API key".

### Step 3: Add API details to FirstPromoter

1. For the newly generated API key, click "View" in the Private Key column.
2. Copy-paste the data from that table to corresponding fields in to the setup form.

### Step 4: Set up the Webhooks

1. Return to Braintree, navigate to Settings > Webhooks, and select "Create New Webhook".
2. In the Destination URL field, enter the 'Webhook Endpoint URL' value from the setup form.
3. Under notifications, check/enable 'Cancelled', 'Charged Successfully', and 'Expired' options only
4. Click on "Create Webhook"
5. Use "Check URL" to make sure you copied the destination URL correctly.

If you don't get any errors it means that FirstPromoter was able to connect successfully to Braintree API.

***If you need to change the Braintree account or switch from the sandbox to the production environment, navigate to Settings > Integrations > View Integrations, select Braintree - Setup, and repeat the steps starting from Step 1.***
