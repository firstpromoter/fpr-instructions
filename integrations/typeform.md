## Integration guide

To integrate Firstpromoter with Typeform, you need to set up a redirect to your website's thank-you/confirmation page to enable capture the lead/referral email from the TypeForm.

To pass the lead/referral email from a TypeForm to the Redirect URL, you need to use the ***Recall Information feature***. Below is how to configure the Recall Information feature:


### Set Up the Redirect URL:

In the settings, go to the Redirect URL section. [See example here](https://help.typeform.com/hc/en-us/articles/4414707303700-Use-variables-in-redirect-links)


Use the Recall Information placeholders to include the email in the redirect URL. [See example here](https://help.typeform.com/hc/en-us/articles/4414707303700-Use-variables-in-redirect-links)


For instance, if your email field is named **email**, you can use **@email** in the URL. [See example here](https://community.typeform.com/build-your-typeform-7/redirect-to-url-passing-email-address-10100)



#### Example Redirect URL Scenario

If your Redirect URL is https://mywebsite.com/thank-you, you can modify it to include the email query parameter like this: https://mywebsite.com/thank-you?email=@email  

[See example here](https://community.typeform.com/build-your-typeform-7/redirect-to-url-passing-email-address-10100)


When redirect is setup and respondent submits the form, they will be redirected to the thank confirmation/thank-you page URL with their email included in the email query parameter.


After the confirmation/thank-you page setup, kindly add the tracking scripts to your website.


### Below are the steps required to add/install the tracking scripts.


#### 1. Main tracking script installation
You need to add/install the main tracking script on your landing page and confirmation/thank-you page (*if you don't have a confirmation/thank-you page, then you need to create one*).

Kindly follow the main tracking script installation guide here: https://docs.firstpromoter.com/guides/tracking-with-fprjs#installation


#### 2. Referral Tracking Script Installation
After adding/installing the main tracking script on the confirmation/thank-you page, you also need to add the Referral tracking script provided below after the main tracking script on the confirmation/thank-you page.


```js Referral tracking script
<script> 
function sendReferralToFirstPromoter() {
  var url = new URL(decodeURI(window.location.href));
  if( url != null && url.searchParams.has("email")){
    var emailFromUrl = url.searchParams.get("email");
    if (window.fpr) {
       window.fpr("referral", { email: emailFromUrl});
    }
  }
}

var docStateCheck = setInterval(function(){
    if (document.readyState === "complete") {
        clearInterval(docStateCheck);
        sendReferralToFirstPromoter();
    }
}, 100);
</script>
```