![Thinkific](/images/thinkific-logo.png)

# Adding FirstPromoter to ThriveCart

To get the best results for tracking on Thinkific it is ideal to set this up on all the marketing pages.


## Main tracking script

1. Go to "Settings".
2. Select Code & Analytics.
3. Add the script below in "Site footer code" section.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

@[trackingtest]("click")

## Referral tracking script

Thinkific provides two ways with which you can set things up.

### Tracking Referrals from orders

If you want to track orders kindly follow the below steps.

1. Go to Settings.
2. Select Code & analytics.
3. Find the  Order tracking code section.
4. Add the below scripts.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;referral&quot;,{email:&quot;{{billing_email}}&quot;});
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

### Tracking Referrals on Signup

If you want to track sign-ups kindly follow the below steps.

1. Go to Settings.
2. Select Code & analytics.
3. Find the Signup tracking code section.
4. Add the below scripts.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;referral&quot;,{email:&quot;{{email}}&quot;});
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

@[trackingtest]("referral")
