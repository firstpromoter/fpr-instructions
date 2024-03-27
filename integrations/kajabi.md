# Adding FirstPromoter to your Kajabi website

To ensure that tracking works as expected this integration has to be done on the Kajabi pages directly. **It doesn't work if Kajabi checkout / form is embedded into another website**.

## Tracking script

1. Go to Settings.
2. Find the "Site Settings" and "Checkout Settings" header page scripts input box.
3. Add the scripts into the header page scripts input box in both sections.
4. Click on save once its added.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
&lt;script src=&quot;https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.0/jquery.min.js&quot; integrity=&quot;sha256-1IKHGl6UjLSIT6CXLqmKgavKBXtr0/jJlaGMEkh+dhw=&quot; crossorigin=&quot;anonymous&quot;&gt;&lt;/script&gt;
&lt;script&gt;
 function set_fprom(){
    console.log(&apos;FPROM loaded&apos;);
    $(document).on(&apos;mousedown&apos;,&apos;a.btn,.checkout-panel-btn,.form-btn&apos;, function(){
      fpr(&quot;referral&quot;,{email: $(&apos;input[type=&quot;email&quot;].form-control&apos;).val(), uid:&quot;&quot;})
    });
 }

if (window.attachEvent){
  window.attachEvent(&apos;onload&apos;, set_fprom);
}else{
  window.addEventListener(&apos;load&apos;, set_fprom, false);
}
&lt;/script&gt;
```

@[trackingtest]("click")

@[trackingtest]("referral")
