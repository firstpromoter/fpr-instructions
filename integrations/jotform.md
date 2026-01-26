## Integration guide

To integrate FirstPromoter with JotForm, you need to set up a redirect to your website's thank-you/confirmation page to capture the lead/referral email from the JotForm submission.

For tracking to work, you first need to add the main tracking script to your landing page. Once you have added the script to the landing page, you need to set up a redirect URL to pass the email from JotForm to the confirmation/thank-you page.


### Steps to pass email data from JotForm to the Confirmation/Thank-you page


#### 1. Get Email Field Name

In the Form Builder, click on the email field you want to pass data from and note the unique name of the field. You can find this in the field properties under the **Advanced** tab.


#### 2. Build the Redirect URL

Construct the URL of your confirmation page and append the form data as query parameters.

For example, if your confirmation/thank-you page URL is `https://example.com/confirmation` and you want to pass the email field, the URL would look like this:

```
https://example.com/confirmation?email={email}
```


#### 3. Set Up Redirect in JotForm

1. In the Form Builder, go to **Settings > Thank You Page**
2. Select **Redirect to an external link after submission**
3. Enter the URL built in step 2. For example: `https://example.com/confirmation?email={email}`


### Below are the steps required to add/install the tracking scripts


#### 1. Main tracking script installation

You need to add/install the main tracking script on your landing page and confirmation/thank-you page (*if you don't have a confirmation/thank-you page, then you need to create one*).



#### 2. Referral Tracking Script Installation

After adding/installing the main tracking script on the confirmation/thank-you page, you also need to add the Referral tracking script provided below after the main tracking script on the confirmation/thank-you page.


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
