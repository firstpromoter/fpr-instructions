# Tracking with FirstPromoter when using Demio

Integrating FirstPromoter with Demio lets you attribute webinar registrations to your affiliates' referral links.

How you add the tracking script depends on where your registration form lives:

- **Demio Registration Page** — you use the registration page hosted by Demio, and add the script through Demio's built-in **Custom Code** feature. No developer needed.
- **Embedded form on your site** — you embed the Demio registration form on your own website, and add the script to your site's pages.

Pick the matching tab below. In both cases a single script handles click tracking and referral tracking, so there's nothing else to install.

## Tracking script

~~~markdown [g1:Demio Registration Page]
Use this if visitors register on the registration page hosted by Demio.

1. Go into your **Events** and click the **Customize** icon.
2. Find the **Integrations** card, select **Custom Code** and click **Settings**.
3. Under **Where do you want to apply this custom change?**, select **Registration Page**.
4. Under **What part of the page do you want the code applied?**, select **Head**.
5. Copy the code below and paste it into the **Custom code** box.
6. Save your changes by clicking **SAVE INTEGRATION**.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;{{ me.company.cid }}&quot;});
fpr(&quot;click&quot;);

document.addEventListener(&quot;submit&quot;, function(e){
  var emailInput = document.getElementById(&quot;email&quot;);
  if (emailInput &amp;&amp; emailInput.value) {
    fpr(&quot;referral&quot;, {email: emailInput.value});
  }
});
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

This one script does everything: `fpr(&quot;click&quot;)` records the affiliate click when a referred visitor lands on the registration page, and the submit listener reports the registrant&apos;s email as a referral.

Repeat these steps for every event you want to track — Custom Code is configured per event.
~~~

~~~markdown [g1:Embedded form on your site]
Use this if you embed the Demio registration form on your own website instead of using the hosted registration page. You&apos;ll need the script in two places.

**1. Base script — add to every page of your site**

This records the affiliate click no matter which page a referred visitor lands on first. Add it to the head section of your entire site, preferably right before the closing `&lt;/head&gt;` tag.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;{{ me.company.cid }}&quot;});
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

**2. Full script — add only to the page where the Demio form is embedded**

This must be on the same page as the Demio embed snippet. It replaces the base script on that page — don&apos;t add both.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;{{ me.company.cid }}&quot;});
fpr(&quot;click&quot;);

document.addEventListener(&quot;submit&quot;, function(e){
  var emailInput = document.getElementById(&quot;email&quot;);
  if (emailInput &amp;&amp; emailInput.value) {
    fpr(&quot;referral&quot;, {email: emailInput.value});
  }
});
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

**Please note that this will not work if the Demio form is loaded inside an iframe** — the script can&apos;t read the email field across the iframe boundary. Use the Demio-hosted registration page instead in that case.
~~~

### Test Click Tracking

@[trackingtest]("click")

### Test Referral Tracking

@[trackingtest]("referral")
