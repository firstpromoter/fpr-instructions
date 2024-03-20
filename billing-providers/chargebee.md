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
10. In the 'Site' field, enter your Chargebee subdomain **(look at the URL bar, if your URL is <https://mycompany.chargebee.com>, your site is 'mycompany')**.
11. Click 'Confirm webhook connection'.


### Create a custom field in Chargebee

The below steps are required if you are using the Chargebee drop-in scripts or hosted pages.

1. Head to Settings > Configure Chargebee.
2. Scroll down till you get to the "Custom fields" section.
3. Ensure you have the Customers tab selected.
4. Select Single line text as shown in the screenshot below.
![chargebee custom fields customers tab](https://gitlab.com/api/v4/projects/55002365/repository/files/images%2Fscreenshots%2Fchargebee-customers-tab.png/raw?ref=main "")
5. This opens a modal with a form.
6. In the field label section put in "tid" as shown in the screenshot below.
![chargebee custom fields modal](https://gitlab.com/api/v4/projects/55002365/repository/files/images%2Fscreenshots%2Fchargebee-custom-fields-modal.png/raw?ref=main "")
7. Click on "Create & Save".
![chargebee custom field after save](https://gitlab.com/api/v4/projects/55002365/repository/files/images%2Fscreenshots%2Fchargebee-custom-field-after-save.png/raw?ref=main "")
8. Return to Settings > Configure Chargebee and select the Self-Service Portal.
9. Select the Fields tab
10. Click on the edit icon next to the tid field we just created.
![chargebee checkout edit](https://gitlab.com/api/v4/projects/55002365/repository/files/images%2Fscreenshots%2Fchargebee-checkout-edit.png/raw?ref=main "")
11. Hide the field so it doesn't show in your checkout and click Apply to save the changes.
![chargebee-hide-field](https://gitlab.com/api/v4/projects/55002365/repository/files/images%2Fscreenshots%2Fchargebee-hide-field.png/raw?ref=main "")
