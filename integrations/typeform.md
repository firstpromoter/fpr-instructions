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


#### Tracking scripts

Add the below scripts to your landing page and confirmation/thank-you page on your website. You may need to find the section where the scripts can be added.


```html Tracking scripts
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;});
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
&lt;script&gt;
function sendReferralToFirstPromoter() {
  var urlString = decodeURI(window.location.href);
  var url = new URL(urlString);

  if(url.searchParams.has(&quot;email&quot;)){
     var emailFromUrl = url.searchParams.get(&quot;email&quot;);
      if (emailFromUrl){
         if (window.fpr) window.fpr(&quot;referral&quot;, { email: emailFromUrl });
      }
  }
}

var stateDocumentCheck = setInterval(function(){
    if (document.readyState === &quot;complete&quot;) {
       clearInterval(stateDocumentCheck);
       sendReferralToFirstPromoter();
    }
}, 100);
&lt;/script&gt;
```

### Test Click Tracking

@[trackingtest]("click")

### Test Referral Tracking

@[trackingtest]("referral")
