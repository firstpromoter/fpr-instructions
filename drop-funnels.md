![Drop Funnels](/images/drop-funnels-logo.png)

# Adding FirstPromoter to your Drop Funnels website

To ensure that tracking works as expected, make sure you add the scripts to every marketing page.

&nbsp;

## Main tracking script

### Adding the scripts to your Drop Funnels website.

1. Click on SEO on the left side menu.
2. Select Google Analytics > Tracking.
3. Add the scripts inside the [HEAD] section.

```html
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("click");
</script>
<script src="https://cdn.firstpromoter.com/fpr.js" async></script>
```

@[trackingtest]("click")

## Referral tracking script

1. Go to Marketing.
2. Select Funnels and click on settings on the funnel step.
3. Select Tracking codes.
4. Add the scripts inside the HEAD tag.

```html
<script>
function set_fprom() {
  jQuery(document).on('mousedown', 'a.fl-button,.fl-builder-submit-btn', function() {
    fpr("referral", {email: jQuery('input[name="fl-subscribe-form-email"],input[name="fl_builder_email"]').val(),uid: ""})
  });
}
if (window.attachEvent) {
  window.attachEvent('onload', set_fprom);
} else {
  window.addEventListener('load', set_fprom, false);
}
</script>
```

@[trackingtest]("referral")
