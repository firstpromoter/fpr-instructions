## Integration guide

To integrate FirstPromoter with Typeform, you need to set up a redirect to your website's thank-you/confirmation page to capture the lead/referral email from the Typeform submission.

For tracking to work, you first need to add the main tracking script to your landing page. Once you have added the script to the landing page, you need to set up a redirect URL to pass the email from Typeform to the confirmation/thank-you page.


### Steps to pass email data from Typeform to the Confirmation/Thank-you page


#### 1. Get Email Field Name

In the Typeform editor, note the name of your email field. By default, Typeform names it **email**, but you may have customized it.


#### 2. Build the Redirect URL

Construct the URL of your confirmation page and append the email using Typeform's **Recall Information** feature with the `@` symbol.

For example, if your confirmation/thank-you page URL is `https://example.com/confirmation` and your email field is named **email**, the URL would look like this:

```
https://example.com/confirmation?email=@email
```

[Learn more about using variables in redirect links](https://help.typeform.com/hc/en-us/articles/4414707303700-Use-variables-in-redirect-links)


#### 3. Set Up Redirect in Typeform

1. In the Typeform editor, go to **Settings > After submit**
2. Select **Redirect to URL**
3. Enter the URL built in step 2. For example: `https://example.com/confirmation?email=@email`


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
