# Adding FirstPromoter to your custom website using Javascript

To get the best results for tracking, It is ideal to set this up on all the marketing or landing pages. **Please note that this setup requires a developer.**

&nbsp;

## Main tracking script

For most websites and JavaScript frameworks, you can simply insert the script on the public `index.html` file so it will be available when the website or framework loads.

1. Find your main index file (index.html, index.php).
2. Locate the `&lt;head&gt;` tag: The `&lt;head&gt;` tag is typically at the top of your  document, right after the opening `&lt;html&gt;` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag `&lt;/head&gt;`
4. Save your changes and publish.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

@[trackingtest]("click")

## Referral tracking script

To track referrals, you'll need to make a request to FirstPromoter to capture the lead. This can mainly be done by calling the "fpr" JavaScript function defined in the main tracking script and inserting the email of the user/lead/customer: `fpr("referral", {email: "user-email"})`

If you can't use the email for privacy reasons, there's another option using "uid",
`fpr(“referral”,{uid:"user-id-in-database”})`

***NB: You need to have the Main tracking script from above available / accessible on this page as well. The below scripts should be placed or called underneath the main tracking script***

Depending on your setup you may need to have a way of getting the email and passing it to the script.

```html
&lt;script&gt;
  var email=&lt;actual user email goes here&gt;;
  window.fpr(&quot;referral&quot;,{email});
&lt;/script&gt;
```

For JavaScript framework like React, Vue, Angular, Ember, Stimulus, etc... you can make the call on the success callback function or even on the onClick handler.

```html
&lt;script&gt;
//... the success callback:
(function(response){
  var email=response.data.email;
  window.fpr(&quot;referral&quot;,{email: email})
}) 
&lt;/script&gt;
```

If you're using a checkout plugin or service that appends the email to the thank-you page like `https://website.com/thank-you?email=user@email.com` you can grab the email from the url and pass  it to the fpr function as shown below.

```html
&lt;script&gt;
function getParam(param){
  return new URLSearchParams(window.location.search).get(param);
}
fpr(&quot;referral&quot;,{email: getParam(&quot;email&quot;)})
&lt;/script&gt;
```

***NB: If you're performing a redirect after calling the function, please double-check it, as redirection blocks any ongoing requests in most browsers (in this case it might be better have a delay or put the script on the redirected page instead).***

@[trackingtest]("referral")
