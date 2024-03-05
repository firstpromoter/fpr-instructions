![CustomJavascript](/images/custom-js-logo.png)

# Adding FirstPromoter to your custom website using Javascript

To get the best results for tracking, It is ideal to set this up on all the marketing or landing pages. **Please note that this setup requires a developer.**

&nbsp;

## Main tracking script

For most websites and JavaScript frameworks, you can simply insert the script on the public `index.html` file so it will be available when the website or framework loads.

1. Find your main index file (index.html, index.php).
2. Locate the `<head>` tag: The `<head>` tag is typically at the top of your  document, right after the opening `<html>` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag `</head>`
4. Save your changes and publish.

```html
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("click");
</script>
<script src="https://cdn.firstpromoter.com/fpr.js" async></script>
```

@[trackingtest]("click")

## Referral tracking script

To track the referrals, you'll need to make a request FirstPromoter to capture the lead. This can mainly be done by calling the “fpr” JavaScript function defined by the main tracking script and insert the email of the user/lead/customer: `fpr(“referral”,{email:"user-email”})`

If you can't use the email for privacy reasons, there's another option using “uid”,
`fpr(“referral”,{uid:"user-id-in-database”})`

***NB: You need to have the Main tracking script from above available / accessible on this page as well. The below scripts should be placed or called underneath the main tracking script***

Depending on your setup you may need to have a way of getting the email and passing it to the script.

```html
<script>
var email=<actual user email goes here>;
window.fpr("referral",{email});
</script>
```

For JavaScript framework like React, Vue, Angular, Ember, Stimulus, etc... you can make the call on the success callback function or even on the onClick handler.

```html
<script>
//... the success callback:
(function(response){
  var email=response.data.email;
  window.fpr("referral",{email: email})
}) 
</script>
```

If you're using a checkout plugin or service that appends the email to the thank-you page like `https://website.com/thank-you?email=user@email.com` you can grab the email from the url and pass  it to the fpr function as shown below.

```html
<script>
function getParam(param){
  return new URLSearchParams(window.location.search).get(param);
}
fpr("referral",{email: getParam("email")})
</script>
```

***NB: If you're performing a redirect after calling the function, please double-check it, as redirection blocks any ongoing requests in most browsers (in this case it might be better have a delay or put the script on the redirected page instead).***

@[trackingtest]("referral")
