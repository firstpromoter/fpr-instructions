# Adding FirstPromoter to your custom website using Javascript

To get the best results for tracking, it is ideal to set this up on all the marketing or landing pages. **Please note that this setup requires a developer.** Remember to  check your browser’s console for any errors. Happy coding! 😊

## Main tracking script

For most websites and JavaScript frameworks, you can simply insert the script on the public `index.html` file so it will be available when the website or framework loads.

1. Find your main index file (index.html, index.php).
2. Locate the `&lt;head&gt;` tag: The `&lt;head&gt;` tag is typically at the top of your  document, right after the opening `&lt;html&gt;` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag `&lt;/head&gt;`
4. Save your changes and publish.

### Vanilla JS, Vue & React

1. Find your main index.html file in your public folder.
2. Locate the `&lt;head&gt;` tag: The `&lt;head&gt;` tag is typically at the top of your  document, right after the opening `&lt;html&gt;` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag </head>  and save.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

### Nuxt 3

For Nuxt 3 you need to use the useHead composable.

1. Create an external file in your public folder with the name `fprmain.js`.
2. Copy and paste the contents below into `fprmain.js`.

```js
// /public/fprmain.js
(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
```

3. On your landing pages or marketing pages you will need to add the script using the useHead composable.

```html
&lt;script setup&gt;
useHead({
  script: [
   { src: &quot;fprmain.js&quot; }
 { async: true,
      src: 'https://cdn.firstpromoter.com/fpr.js',
    }, 
  ],
});
&lt;/script&gt;
```

### NextJS

For NextJS you need to add the script to the `_document.tsx` file.

1. Create an external file in your public folder with the name `fprmain.js`.
2. Copy and paste the contents below into `fprmain.js`.

```js
// /public/fprmain.js
(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
```

3. Add fprmain.js as a `&lt;script&gt;` tag inside the Head tag in _document.tsx and then add `&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; /&gt;` as well.

```js
import { Html, Head, Main, NextScript } from &apos;next/document&apos;

export default function Document() {
  return (
    &lt;Html&gt;
      &lt;Head&gt;
        &lt;script src=&quot;fprmain.js&quot;/&gt;
        &lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; /&gt;
      &lt;/Head&gt;
      &lt;body&gt;
        &lt;Main /&gt;
        &lt;NextScript /&gt;
      &lt;/body&gt;
    &lt;/Html&gt;
  )
}
```

@[trackingtest]("click")

## Referral tracking script

To track referrals, you'll need to make a request to FirstPromoter to capture the lead. This can mainly be done by calling the "fpr" JavaScript function defined in the main tracking script and inserting the email of the user/lead/customer: `fpr("referral", {email: "user-email"})`

If you can't use the email for privacy reasons, there's another option using "uid",
`fpr(“referral”,{uid:"user-id-in-database”})`

***NB: You need to have the Main tracking script from above available / accessible on this page as well. The below scripts should be placed or called underneath the main tracking script.*** 

***The placement of this code may vary depending on your website. For basic use cases where vanilla JavaScript or jQuery is used, it can be placed in the `<head>` section of your website and triggered by an event such as a button click. However for more complex scenarios or when using JavaScript frameworks it is best incorporated within your code base and invoked after an event is successful, such as a success callback for sign up.***

Depending on your setup, you will need to:

1. Find the section in your code where you can get access to the email/uid of the current user. Preferably the sign up page, opt-in form or checkout page.
2. Capture the email and pass it to the `fpr` function like this:  `fpr("referral", {email: <user-email-goes-here>})`.
3. Below is an example of how the code may look like.

```html
&lt;script&gt;
  var email=&lt;actual@email.com&gt;;
  window.fpr(&quot;referral&quot;,{email});
&lt;/script&gt;
```

If you are having a simple form on your website you can capture the email from the input field and make the request when the submit button is pressed. Below is an example.

&lt;script&gt;
  const emailInput = document.querySelector(&apos;input[name=&quot;email&quot;]&apos;)
  const submitButton = parentForm.querySelector(&quot;button[type=&apos;submit&apos;]&quot;);
  //we don&apos;t use the click event since you may be using that for something else
  [&quot;mousedown&quot;, &quot;touchstart&quot;].forEach(function (event) {
    submitButton.addEventListener(event, function () {
      if (validateEmail(emailInput.value)) {
        fpr(&quot;referral&quot;, {
          email: emailInput.value,
        });
      }
    });
  });
&lt;/script&gt;

For JavaScript frameworks like React, Vue, Angular, Ember, Stimulus, etc... you can make the call on a success callback function or even on a click handler.

```html
&lt;script&gt;
//... the success callback:
(function(response){
  var email=response.data.email;
  window.fpr(&quot;referral&quot;,{email: email})
}) 
&lt;/script&gt;
```


If you're using a checkout plugin or service that appends the email to the thank-you page like `https://website.com/thank-you?email=user@email.com`, you can grab the email from the url and pass it to the fpr function as shown below.

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
