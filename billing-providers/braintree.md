![BrainTree](/images/logos/braintree.png)

# Connecting FirstPromoter with Braintree

FirstPromoter allows you to automatically track sales, upgrades and cancellations from Braintree.

***Important note: Because of Braintree Webhooks limitation, FirstPromoter can't automatically handle refunds, all other functions are working corectly. In case of a refund, you just need to "Deny" the commission/reward of the affiliate.***

## Setting Up

To get started, you need to follow the steps below:

For added security, you can create a new User Role on Braintree that allows only read operations. You can skip to Step 2 if you are not concerned about this or you are in Braintree Sandbox environment.

### Step 1: Create a Read Only User Role(optional)

1. Login as admin to your Braintree account and go to Settings > User and Roles > Manage Roles > New
2. Give a role name like Read-Only
3. Uncheck all permissions except: Download Transactions with Masked Payment Data, Download Vault Records with Masked Payment Data, Download Subscription Records, Manage Webhooks
4. Click 'Create Role'
5. Now go to Settings > Users and roles > New user. Give the user API Access, assign the read only role and assign access to the merchant accounts
6. Now logout of Braintree and log back in as this new 'read only' user.

### Step 2: Create a new API key

1. Login to Braintree, navigate to Account > My User (on top menu) and scroll down until you see:
2. Click on View Authorizations. Once you are on the API keys section, click on 'Generate API key'.

### Step 3: Add API details to FirstPromoter

1. On the new API key generated, click "View" in the Private Key column.
2. Copy-paste the data from that table to corresponding fields on FirstPromoter Braintree Setup form.

### Step 4: Set up the Webhooks

1. Go back to Braintree, go to Settings > Webhooks and click 'Create New Webhook'
2. On the Destination URL field add the 'Webhook Endpoint URL' value from FirstPromoter Braintree Setup
3. On Notifications, check only 'Cancelled', 'Charged Successfully' and 'Expired'
4. Click 'Create Webhook'
5. Click 'Check URL' to make sure you copy-pasted the destination url correctly.
