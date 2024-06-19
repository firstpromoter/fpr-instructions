# Connecting FirstPromoter with Paddle

FirstPromoter allows you to automatically track sales, refunds, upgrades and cancellations from Paddle.

## Setting Up Paddle Billing

To get started, you need to follow the below steps:

### Set up Paddle Notifications

To set the Webhooks, you will have to:

1. Login to Paddle > Developer tools in the sidebar > Notifications
2. Click on New Destination
3. In the popup that comes up, set your description and add in the URL provided from FirstPromoter.

The events required by FirstPromoter are **​transaction.completed**, **transaction.cancelled**, **subscription.cancelled**, **subscription.created** and **adjustment.updated**, so please make sure these webhook events are enabled.


## Setting Up Paddle Classic

To get started, you need to follow the below steps:

### Set up Webhooks

To set the Webhooks, you will have to:

1. Login to Paddle > Developer tools in the sidebar > Events > click on "+ Add new endpoint"
2. Add the new field named "Webhook Endpoint URL" from FirstPromoter.

The events required by FirstPromoter are **payment_succeeded**, **payment_refunded**, **subscription_payment_succeeded**, **subscription_payment_refunded** and **subscription_cancelled**, so please make sure these webhook events are enabled.

### Set up Public Key

To get the public key from Paddle, go to Developer tools on the sidebar > Public key.

Make sure you enter the public key from Paddle in the integration form and confirm the webhook connection.

**PLEASE DO NOT REMOVE ANYTHING** from the public key. Just copy and paste it entirely as it shows on Paddle, including `-----BEGIN PUBLIC KEY-----` and `-----END PUBLIC KEY-----`, otherwise you'll get a 500 error.