![Drop Funnels](/images/logos/dropfunnels.png)

# Adding FirstPromoter to your Drop Funnels website

To ensure that tracking works as expected, make sure you add the scripts to every marketing page.

## Main tracking script

1. Click on SEO on the left side menu.
2. Select Google Analytics > Tracking.
3. Add the scripts inside the [HEAD] section.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

@[trackingtest]("click")

## Referral tracking script

1. Go to Marketing.
2. Select Funnels and click on settings on the funnel step.
3. Select Tracking codes.
4. Add the scripts inside the HEAD tag.

```html
&lt;script&gt;
function set_fprom() {
  jQuery(document).on(&apos;mousedown&apos;, &apos;a.fl-button,.fl-builder-submit-btn&apos;, function() {
    fpr(&quot;referral&quot;, {email: jQuery(&apos;input[name=&quot;fl-subscribe-form-email&quot;],input[name=&quot;fl_builder_email&quot;]&apos;).val(),uid: &quot;&quot;})
  });
}
if (window.attachEvent) {
  window.attachEvent(&apos;onload&apos;, set_fprom);
} else {
  window.addEventListener(&apos;load&apos;, set_fprom, false);
}
&lt;/script&gt;
```

@[trackingtest]("referral")
