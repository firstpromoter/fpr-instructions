# Working with FirstPromoter and Calendly

This integration is for users who have custom websites and have Calendly added. **You must be on the Calendly Professional Plan. It also requires you to have a thank-you page, which you will redirect to after a user books an appointment.**


## Main tracking script

1. On your website, add the below scripts to all your landing or marketing pages. Preferably in the head section of your entire website or on your landing pages.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

2. Go to your Calendly home page.
3. Select the desired event.
4. Expand the **Confirmation Page** section.
5. In the “On confirmation” section, choose “**Redirect to an external site**”.
![calendly screenshot](https://gitlab.com/api/v4/projects/55002365/repository/files/images%2Fscreenshots%2Fcalendly-setup.png/raw?ref=main "")

1. Enter your “Thank You” page URL in the **Redirect URL** section.
2. Check the option “**Pass event details to your redirected page**” to include the lead's email in the “Thank You” page URL.
3. Click Save & Close.


@[trackingtest]("click")

## Referral tracking script

Add the below script to your thank-you page preferably in the head section.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
&lt;script&gt;
    function sendReferralToFirstPromoter() {
      if (window.fpr) {
          var urlString = decodeURI(window.location.href);
          var emailFromUrl = new URLSearchParams(urlString).get(&quot;invitee_email&quot;);
          if (emailFromUrl) {
            fpr(&quot;referral&quot;, { email: emailFromUrl });
          }
      }
    }
    if (window.attachEvent) {
      window.attachEvent(&quot;onload&quot;, sendReferralToFirstPromoter);
    }
    else {
      window.addEventListener(&quot;load&quot;, sendReferralToFirstPromoter, false);
    }
&lt;/script&gt;
```

@[trackingtest]("referral")
