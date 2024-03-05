![Kickpages](/images/kick-pages-logo.png)

# Adding FirstPromoter to Kickpages

To get the best results, make sure you add the following script globally on the HEAD section of every public or marketing page on your website.


## Main tracking script

1. On your Kickpages dashboard, go to the  projects page
2. Hover on the settings icon under the profile picture
3. Select Includes  
4. Add the below scripts to the first field and save

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

@[trackingtest]("click")

## Referral tracking script

1. Go back to the Projects page.
2. Click on your project.
3. Click Edit Page and select Settings on top right.
4. Click on Custom Includes.
5. Add the script in Code for Head Tag.

```html
&lt;script src=&quot;https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.0/jquery.min.js&quot; integrity=&quot;sha256-1IKHGl6UjLSIT6CXLqmKgavKBXtr0/jJlaGMEkh+dhw=&quot; crossorigin=&quot;anonymous&quot;&gt;
&lt;/script&gt;
&lt;script&gt;
  function set_fprom(){
    console.log(&apos;loaded&apos;);
    $(document).on(&apos;click&apos;,&apos; a[name=&quot;btnSubmit&quot;]&apos;, function(){
      fpr(&quot;referral&quot;,{email: $(&apos;input[name=&quot;orderFormEmail&quot;]&apos;).val(), uid:&quot;&quot;})
    });
  }
  if (window.attachEvent){
    window.attachEvent(&apos;onload&apos;, set_fprom);
  }else{
    window.addEventListener(&apos;load&apos;, set_fprom, false);
  }
&lt;/script&gt;
```

@[trackingtest]("referral")