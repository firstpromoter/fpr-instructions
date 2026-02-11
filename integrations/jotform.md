# Tracking with FirstPromoter when using JotForm

To integrate FirstPromoter with JotForm, you need to set up a redirect to your **website's thank-you/confirmation page** to capture the lead/referral email from the JotForm submission.

For tracking to work, you first need to add the tracking script to your landing page and thank you page. Once you have added the script to the landing page, you need to set up a redirect URL to pass the email from JotForm to the confirmation/thank-you page on your website.



## Steps to pass email data from JotForm to the Confirmation/Thank-you page
These steps are important in order to capture the referrals from your website when they complete the form.

### 1. Get Email Field Name

In the Form Builder, click on the email field you want to pass data from and note the unique name of the field. You can find this in the field properties under the **Advanced** tab.


### 2. Build the Redirect URL

Construct the URL of your confirmation page and append the form data as query parameters.

For example, if your confirmation/thank-you page URL is `https://your-website.com/thankyou` and you want to pass the email field, the URL would look like this:

```
https://your-website.com/thankyou?email={email}
```


### 3. Set Up Redirect in JotForm

1. In the Form Builder, go to **Settings > Thank You Page**
2. Select **Redirect to an external link after submission**
3. Enter the URL built in step 2. For example: `https://your-website.com/thankyou?email={email}`


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
