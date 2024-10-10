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



## Referral tracking script

~~~markdown [g2:Embedded form in custom website]
To track referrals using the HubSpot form you can take advantage of the `onFormSubmit` event and use that in making the request to track the referrals. You will need to modify the `hbspt.forms.create` scripts as shown below. 

**Please note that if you will need to edit the `hbspt.forms.create` code on your website. Your developer may be required to assist you if you are not certain on how it was added**

``` javascript
  onFormSubmit: function ($form) {
        var email = $form.querySelector('input[name="email"]').value;
        fpr("referral", {email});
    },

```

Your full code should look like this

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

~~~

~~~markdown [g2:HubSpot Website]

To track referrals using the HubSpot form
1. On your HubSpot Dashboard navigate to your `Website pages` and click on the page you want to add the scripts to.
2. Select Settings > Click on Advanced in the top menu.
3. Copy the code below and insert it into the Head HTML section.

**Please note that if this page is different from the one which has the main tracking script You may need to add the main tracking script again before adding this.**

&lt;script&gt;

  function validateEmail(email) {
    var emailReg = /^([\w-\.]+@([\w-]+\.)+[\w-]{2,4})?$/;
    if (email) return emailReg.test(email);
    return false;
  }

  function sendLeadToFP(){
      var emailInput = document.querySelector(&apos;input[type=&quot;email&quot;],input[name=&quot;email&quot;]&apos;);
      var submitButton = document.querySelector(&quot;button[type=&apos;submit&apos;],input[type=&apos;submit&apos;]&quot;);
      
      //use the mousedown or touchstart event to prevent overwriting the default click event.
      [&quot;mousedown&quot;, &quot;touchstart&quot;].forEach(function (event) {
        submitButton.addEventListener(event, function () {
          if (validateEmail(emailInput.value)) {
            fpr(&quot;referral&quot;, {
              email: emailInput.value,
            });
          }
        });
      });
  }

  if (window.attachEvent) {
      window.attachEvent(&quot;onload&quot;, sendLeadToFP);
  } else {
      window.addEventListener(&quot;load&quot;, sendLeadToFP, false);
  }
&lt;/script&gt;
~~~

@[trackingtest]("referral")