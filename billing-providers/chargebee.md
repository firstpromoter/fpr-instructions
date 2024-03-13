# Connecting FirstPromoter with Chargebee

FirstPromoter allows you to automatically track sales, refunds, upgrades, and cancellations from Chargebee.

## Setting Up

To get started, you need to:

1. Login to your Chargebee Dashboard.
2. Go to Settings > Webhook Settings.
3. Click the 'Add new webhook' button on the top right (if it's visible).
4. Set the Webhook name as something like 'FirstPromoter'.
5. Paste the Webhook Endpoint URL value from the FirstPromoter integration setup into the Webhook URL.
6. Select API version - V2.
7. Select for Events only: Customer Created, Payment Succeeded, Payment Refunded, Subscription Cancelled, Subscription Deleted.
8. Check 'Exclude card information from webhook call'.
9. Click 'Create Webhook'.
10. In the 'Site' field, enter your Chargebee subdomain **(look at the URL bar, if your URL is https://mycompany.chargebee.com, your site is 'mycompany')**.
11. Click 'Confirm webhook connection'.
