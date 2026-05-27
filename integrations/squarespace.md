# Adding FirstPromoter to your Squarespace website

Code Injection in Squarespace applies site-wide. If you only want tracking on specific landing or marketing pages, you can use per-page injection instead. No developer is required — the setup is copy-paste only.

## Main tracking script

1. Go to the Squarespace admin panel.
2. Navigate to **Settings > Advanced > Code Injection**.
3. Paste the script below into the **Header** field.
4. Click **Save**.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;{{ me.company.cid }}&quot;});
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

**For specific pages only:** Go to **Pages > [page] > gear icon > Advanced > Page Header Code Injection** and paste the script there instead.

@[trackingtest]("click")

## Referral tracking script

This script listens for Squarespace form submissions — including account signup forms and newsletter blocks — and calls `fpr("referral", ...)` to track the referred user's email.

Add this script **below** the main tracking script, also in the Header Code Injection field, or paste it directly after it.

```html
&lt;script&gt;
document.addEventListener(&apos;DOMContentLoaded&apos;, function() {
  function trackSquarespaceSignup() {
    var accountForms = document.querySelectorAll(&apos;form[data-form-id*=&quot;account&quot;], .customer-account-form, .newsletter-signup-form&apos;);
    accountForms.forEach(function(form) {
      form.addEventListener(&apos;submit&apos;, function() {
        var emailInput = form.querySelector(&apos;input[type=&quot;email&quot;], input[name=&quot;email&quot;]&apos;);
        if (emailInput && emailInput.value) {
          fpr(&quot;referral&quot;, { email: emailInput.value });
        }
      });
    });
  }

  trackSquarespaceSignup();

  var newsletterBlocks = document.querySelectorAll(&apos;.newsletter-block, [data-block-type=&quot;newsletter&quot;]&apos;);
  newsletterBlocks.forEach(function(block) {
    var form = block.querySelector(&apos;form&apos;);
    if (form) {
      form.addEventListener(&apos;submit&apos;, function() {
        var emailInput = form.querySelector(&apos;input[type=&quot;email&quot;]&apos;);
        if (emailInput && emailInput.value) {
          fpr(&quot;referral&quot;, { email: emailInput.value });
        }
      });
    }
  });
});
&lt;/script&gt;
```

**NB:** The form selectors (`form[data-form-id*="account"]`, `.newsletter-block`, etc.) target standard Squarespace form elements. Custom forms may require selector adjustments.

@[trackingtest]("referral")
