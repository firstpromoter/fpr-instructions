![Kajabi](/images/kajabi-logo.png)

# Adding FirstPromoter to your Kajabi website

To ensure that tracking works as expected this integration has to be done on the Kajabi pages directly. It doesn't work if Kajabi checkout / form is embedded into another website.

&nbsp;

## Tracking script

1. Go to Settings.
2. Find the "Site Settings" and "Checkout Settings" header page scripts input box.
3. Add the scripts into the header page scripts input box in both sections.
4. Click on save once its added.

```html
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("click");
</script>
<script src="https://cdn.firstpromoter.com/fpr.js" async></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.0/jquery.min.js" integrity="sha256-1IKHGl6UjLSIT6CXLqmKgavKBXtr0/jJlaGMEkh+dhw=" crossorigin="anonymous"></script>
<script>
 function set_fprom(){
    console.log('FPROM loaded');
    $(document).on('mousedown','a.btn,.checkout-panel-btn,.form-btn', function(){
      fpr("referral",{email: $('input[type="email"].form-control').val(), uid:""})
    });
 }

if (window.attachEvent){
  window.attachEvent('onload', set_fprom);
}else{
  window.addEventListener('load', set_fprom, false);
}
</script>
```

@[trackingtest]("click")

@[trackingtest]("referral")
