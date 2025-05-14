# Adding FirstPromoter when using Stripe payment links

To get the best results for tracking when using Stripe payment links, add the script to all pages where **Stripe payment links** are available.

**Note: These set of scripts are for links like <https://buy.stripe.com/xxxxx> that are directly on your page. If you do not use these stripe payment links directly  on your page this is not ideal for your use case.**

**You can reach out to us using the chat icon in the lower right corner of the page if you are not sure which option to pick.**

## Tracking script

1. Find the section on your website where you can add scripts, preferably in the head section of your website.
2. Add the code below to the head section.

***NB: If you are using your custom domain with stripe, you will need to change the link in the code from <https://buy.stripe.com/> to what is used for your domain.***

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
&lt;script&gt;
    function getFPTid() {
      return window.FPROM &amp;&amp; window.FPROM.data.tid;
    }
    function initializeFPRPaymentLinks() {
      console.log(&quot;initialized fpr on payment links&quot;);
      setTimeout(function () {
        var stripePaymentLinks = document.querySelectorAll(
          &apos;a[href^=&quot;https://buy.stripe.com/&quot;]&apos;
        );
        stripePaymentLinks.forEach(function (link) {
          // Get current url
          var oldStripePaymentUrl = link.getAttribute(&quot;href&quot;); 
          // Get the tid
          var tid = getFPTid();
          if (tid) {
            var url = new URL(oldStripePaymentUrl);
            url.searchParams.set(&apos;client_reference_id&apos;, tid);
            link.setAttribute(&quot;href&quot;, url.toString());
          }
        });
      }, 800);
    }
    if (window.attachEvent) {
      window.attachEvent(&quot;onload&quot;, initializeFPRPaymentLinks);
    } else {
      window.addEventListener(&quot;load&quot;, initializeFPRPaymentLinks, false);
    }
  &lt;/script&gt;
```

@[trackingtest]("click")

@[trackingtest]("referral")
