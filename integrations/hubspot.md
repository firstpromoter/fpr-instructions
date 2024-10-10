# Adding FirstPromoter to your HubSpot form 

This guide is for users who use HubSpot forms on their website.

To get the best results for tracking, it is ideal to set this up on all the marketing or landing pages.

## Main tracking script

~~~markdown [g1:Embedded form in custom website]

For most websites, you can simply insert the script on the public `index.html` file so it will be available to all your pages.

**Please note that this will not work with HubSpot forms loaded in an iframe**

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
~~~

~~~markdown [g1:HubSpot Website]
If your website is hosted on HubSpot directly and you are using HubSpot forms on the page

1. On your HubSpot Dashboard navigate to your `Website pages` and click on the page you want to add the scripts to.
2. Select Settings > Click on Advanced in the top menu.

![hubspot menu](https://gitlab.com/api/v4/projects/55002365/repository/files/images%2Fscreenshots%2Fhubspot-settings-advanced.png/raw?ref=main "")

3. Copy the code below and insert it into the Head HTML section.

![hubspot headhtml](https://gitlab.com/api/v4/projects/55002365/repository/files/images%2Fscreenshots%2Fhubspot-head-html.png/raw?ref=main "")

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```
~~~

@[trackingtest]("click")



@[trackingtest]("referral")