![RubyOnRails](/images/custom-ruby-on-rails-logo.png)

# Adding FirstPromoter to your Rails website

To get the best results for tracking, It is ideal to set this up on all the marketing or landing pages. Please note that this process mainly requires a developer.  Remember to always check your browser’s console for any errors or issues. Happy coding! 😊
**Please note that this setup requires a developer.**


## Main tracking script

1. Locate the layout file where you want to add the script. This is typically located in `app/views/layouts/application.html.erb`.
2. Locate the `<head>` tag. It is typically at the top of your layout document, right after the opening `<html>` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag `</head>`.
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

Tracking referrals can be easily done by adding this JavaScript code snippet `fpr("referral",{email: "user-email"}` on the view/template rendered after user signs up or makes the purchase and passing the user email to it.

**If your main tracking script is not available or accessible on this page you will need to add it here as well.**
***Make sure it is NOT placed on confirmation or thank you pages where old users can visit again.***

Similar to the main tracking script,

1. Locate the layouts file where you want to add the script.
2. Find the head tag.
3. Based on how you capture your emails, use any of the scripts below.

```html
<!--if you store the user email on a session variable--> 
&lt;script&gt;
fpr(&quot;referral&quot;,{email:&quot;&lt;%=session[:email]%&gt;&quot;})
&lt;/script&gt;

<!--if current_user is available you can render the email like this: -->
&lt;script&gt;
fpr(&quot;referral&quot;,{email:&quot;&lt;%=current_user.email%&gt;&quot;})
&lt;/script&gt;
```

### Some ideas for the integration

- If you already log the user in, you can use the currently authenticated user to render the email on the script.
- If you don't have the user logged in, you can store the email on a session variable and render it on the next page where user gets redirected to.
- If you're creating the customer on the billing provider via a library/API, on the rendered view/template you can also pass the billing provider customer id (Stripe customer id for ex.) as 'uid' and even skip the email altogether `fpr("referral",{uid:"cus_43gGBdr5hEkh571Hg"})`.


@[trackingtest]("referral")