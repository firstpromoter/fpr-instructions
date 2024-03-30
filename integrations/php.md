# Adding FirstPromoter to your custom PHP website

To get the best results for tracking, it is ideal to set this up on all the marketing or landing pages. **Please note that this setup requires a developer.** Remember to  check your browser’s console for any errors. Happy coding! 😊

## Main tracking script

For most PHP websites, you can simply insert the script on the public index.php file so it will be available when the page loads.

### Vanilla PHP

1. Locate the PHP file where you want to add the script. This could be the index.php or any other .php file depending on your project structure
2. Locate the `&lt;head&gt;` tag. It is typically at the top of your PHP document, right after the opening `&lt;html&gt;` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag `&lt;/head&gt;`.
4. Save your changes.

### Laravel

In Laravel, you typically add scripts in your blade template files.

1. Locate the Blade file where you want to add the script. This could be a main layout file like app.blade.php or any other .blade.php  file depending on your project structure.
2. Locate the `&lt;head&gt;` tag. It is typically at the top of your PHP document, right after the opening `&lt;html&gt;` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag `&lt;/head&gt;`.
4. Save your changes.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

@[trackingtest]("click")

## Referral tracking script

Tracking referrals can be easily done by adding this JavaScript code snippet `fpr("referral",{email: "user-email"})` on the view/template rendered after the user signs up or makes the purchase and passing the user's email to it.
*Make sure it is NOT placed on confirmation or thank you pages where old users can visit again.*

### Vanilla PHP

Similar to the main tracking script.

1. Locate the PHP file where you want to add the script.
2. Find the head tag.
3. Use a script similar to the below to send the lead details to FirstPromoter. This mainly needs you to capture your email and pass that to the script as a variable  `&lt;script&gt;fpr(&quot;referral&quot;,{email: &quot;&lt;?php echo $email ?&gt;&quot;})&lt;/script&gt;`

### Laravel

Similar to the main tracking script

1. Locate the Blade file where you want to add the script.
2. Find the head tag  
3. Based on how you capture your emails use any of the scripts below

```html
&lt;!-- // if authenticated user is available you can render the email like this: --&gt;
&lt;script&gt;
fpr(&quot;referral&quot;,{email:&quot;&#123;&#123; Auth::user()-&gt;email &#125;&#125;&quot;})
&lt;/script&gt;

&lt;!--  if you store the user email on a session variable --&gt;
&lt;script&gt;
fpr(&quot;referral&quot;,{email:&quot;&#123;&#123; session(&apos;email&apos;) &#125;&#125;&quot;})
&lt;/script&gt;

&lt;!-- if you use the &quot;uid&quot; and don&apos;t want to provide the email, you can skip it entirely: --&gt;
&lt;script&gt;
fpr(&quot;referral&quot;,{uid:&quot;&#123;&#123; $user-&gt;id &#125;&#125;&quot;})
&lt;/script&gt;
```

The tracking of the actual sale will be handled automatically by the billing provider integration or our API (in case you'll use that for sales tracking).

### Some ideas for the integration

- If you already log the user in, you can use the currently authenticated user to render the email on the script.
- If you don't have the user logged in, you can store the email on a session variable and render it on the next page where user gets redirected to.
- If you're creating the customer on the billing provider via a library/API, on the rendered view/template you can also pass the billing provider customer id (Stripe customer id for ex.) as 'uid' and even skip the email altogether `fpr("referral",{uid:"cus_43gGBdr5hEkh571Hg"})`.

@[trackingtest]("referral")
