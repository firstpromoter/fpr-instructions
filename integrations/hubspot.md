# Adding FirstPromoter to your HubSpot form 

This guide is for the [embedded HubSpot forms](https://developers.hubspot.com/docs/cms/building-blocks/forms ""). **Please note that this will not work with HubSpot forms loaded in an iframe**

To get the best results for tracking, it is ideal to set this up on all the marketing or landing pages.

## Main tracking script

For most websites, you can simply insert the script on the public `index.html` file so it will be available to all your pages.

1. Find your main index file (index.html, index.php).
2. Locate the `&lt;head&gt;` tag: The `&lt;head&gt;` tag is typically at the top of your document, right after the opening `&lt;html&gt;` tag.
3. Add the code below into the head section of your website, preferably before the closing head tag `&lt;/head&gt;`.
4. Save your changes and publish.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

@[trackingtest]("click")

## Referral tracking script

To track referrals using the HubSpot form you can take advantage of the `onFormSubmit` event and use that in making the request to track the referrals. You will need to modify the `hbspt.forms.create` scripts as shown below.

```html
&lt;script charset=&quot;utf-8&quot; type=&quot;text/javascript&quot; src=&quot;//js.hsforms.net/forms/embed/v2.js&quot;&gt;&lt;/script&gt;
&lt;script&gt;
  hbspt.forms.create({
    region: &quot;na1&quot;,
    ...

    onFormSubmit: function ($form) {
        var email = $form.querySelector('input[name="email"]').value;
        fpr("referral", {email});
    },

  });
&lt;/script&gt;
```