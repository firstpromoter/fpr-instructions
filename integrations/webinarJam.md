# Tracking with FirstPromoter when using WebinarJam registration form


To integrate FirstPromoter with WebinarJam registration form, you need to set up a redirect to your **website's thank-you/confirmation page** to capture the lead/referral email from the WebinarJam registration form submission.

For tracking to work, you first need to add the main tracking script to your landing page. Once you have added the script to the landing page, you need to set up a redirect URL to pass the email from WebinarJam form to the confirmation/thank-you page on your website.


## Steps to pass email data from WebinarJam registration form to the Confirmation/Thank-you page


### 1. Setting up the Redirect

- Go to the **Thank You** step in the webinar **configuration** wizard

- Open the **Default vs Custom confirmation** page module and select **Your own custom page**

- Enter the thank-you/confirmation page URL in **Your Post-registration confirmation page** field. This is where you need to enter your thank-you/confirmation page URL. For example: `https://your-website.com/thankyou`

- Select **Send register information and webinar information** if it is not already selected.

See this [article](https://support.webinarjam.com/support/solutions/articles/153000168593-custom-confirmation-page) for more information.


### Tracking scripts

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

  if(url.searchParams.has(&quot;wj_lead_email&quot;)){
     var emailFromUrl = url.searchParams.get(&quot;wj_lead_email&quot;);
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
