# Integrating FirstPromoter with your website using our API

To get the best results for tracking, it is ideal to set this up on all the marketing or landing pages. **Please note that this setup requires a developer.** Remember to  check your browser’s console for any errors. Happy coding! 😊

## Main tracking script

For most websites and JavaScript frameworks, you can simply insert the script on the public `index.html` file so it will be available when the website or framework loads.

~~~markdown [g1:JavaScript]

1. Find your main index file (index.html, index.php).
2. Locate the `&lt;head&gt;` tag: The `&lt;head&gt;` tag is typically at the top of your  document, right after the opening `&lt;html&gt;` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag `&lt;/head&gt;`
4. Save your changes and publish.

  ```html
  &lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
  fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
  fpr(&quot;click&quot;);
  &lt;/script&gt;
  &lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
  ```
~~~

~~~markdown [g1:Vue]

1. Find your main index.html file in your public folder.
2. Locate the `&lt;head&gt;` tag: The `&lt;head&gt;` tag is typically at the top of your  document, right after the opening `&lt;html&gt;` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag `&lt;/head&gt;` and save.

  ```html
  &lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
  fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
  fpr(&quot;click&quot;);
  &lt;/script&gt;
  &lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
  ```

~~~

~~~markdown [g1:Nuxt]

For Nuxt you need to use the useHead composable.

1. Create an external file in your public folder with the name `fprmain.js`.
2. Copy and paste the contents below into `fprmain.js`.

  ```js
  // /public/fprmain.js
  (function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
  fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
  fpr(&quot;click&quot;);
  ```

3. On your landing pages or marketing pages you will need to add the script using the useHead composable.

  ```html
  &lt;script setup&gt;
  useHead({
    script: [
    { src: &quot;fprmain.js&quot; }
  { async: true,
        src: &quot;https://cdn.firstpromoter.com/fpr.js&quot;,
      }, 
    ],
  });
  &lt;/script&gt;
  ```
~~~

~~~markdown [g1:React]
1. Find your main index.html file in your public folder.
2. Locate the `&lt;head&gt;` tag: The `&lt;head&gt;` tag is typically at the top of your  document, right after the opening `&lt;html&gt;` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag `&lt;/head&gt;` and save.


  ```html
  &lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
  fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
  fpr(&quot;click&quot;);
  &lt;/script&gt;
  &lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
  ```

~~~

~~~markdown [g1:Next]
For NextJS you need to add the script to the `_document.tsx` file.

1. Create an external file in your public folder with the name `fprmain.js`.
2. Copy and paste the contents below into `fprmain.js`.

```js
// /public/fprmain.js
(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
```

3. Add `fprmain.js` as a `&lt;script&gt;` tag inside the Head tag in _document.tsx and then add `&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; /&gt;` as well.

```js
import { Html, Head, Main, NextScript } from &apos;next/document&apos;

export default function Document() {
  return (
    &lt;Html&gt;
      &lt;Head&gt;
        &lt;script src=&quot;fprmain.js&quot;/&gt;
        &lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; /&gt;
      &lt;/Head&gt;
      &lt;body&gt;
        &lt;Main /&gt;
        &lt;NextScript /&gt;
      &lt;/body&gt;
    &lt;/Html&gt;
  )
}
```
~~~


~~~markdown [g1:Angular]
1. Find your main index.html file in your src folder.
2. Locate the `&lt;head&gt;` tag: The `&lt;head&gt;` tag is typically at the top of your  document, right after the opening `&lt;html&gt;` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag `&lt;/head&gt;` and save.


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

To track referrals using the API, you'll need to have access to the browser cookies. Once the main tracking script is implemented, two cookies, namely `_fprom_tid` and `_fprom_ref`, are set upon visiting the referral link. Both cookies can be used in making your API requests; however, to prevent multiple tracking, it is recommended to use the `_fprom_tid`. This include a check to determine if a browser session has already been tracked, ensuring that tracking occurs only once.

1. Get your API key from your Settings > Integrations tab.
2. On your backend, retrieve the `_fprom_tid` cookie.

```js {noCopy}
//backend.js
const cookieParser = require(&apos;cookie-parser&apos;); 
...
app.use(cookieParser());
const tid = req.cookies[&apos;_fprom_tid&apos;];
```

3. With the cookie retrieved, make a POST request to the API endpoint `https://firstpromoter.com/api/v1/track/signup`  together with the following parameters.

```plaintext {noCopy}
Parameter     Required                  Description

email         yes if uid is null        email of the lead/sign-up
uid           yes if email is null      user id of the user in your database
tid           yes if ref_id is null     visitor tracking id.
ref_id        yes if tid is null        default referral id of the promoter.
ip            no                        IP of the visitor

```

**Note:** the request content type for our API is not JSON, it's `application/x-www-form-urlencoded`.

4. The full code will look like this.

```js {noCopy}

//backend.js
const axios = require('axios');
...
//this code can go into your sign up flow
// to make this cleaner you can extract it into a function

const email = &apos;example@example.com&apos; //replace with actual email
const tid = req.cookies[&apos;_fprom_tid&apos;];

const params = new URLSearchParams();
params.append(&quot;email&quot;, email);
params.append(&quot;tid&quot;, tid);

axios
    .post(&quot;https://firstpromoter.com/api/v1/track/signup&quot;, params, {
      headers: {
        &quot;Content-Type&quot;: &quot;application/x-www-form-urlencoded&quot;,
        &quot;x-api-key&quot;: &quot;your api key here&quot;,
      },
    })
    .then(function (response) {
      //any action if the request is successful
      console.log(JSON.stringify(response.data));
    })
    .catch(function (error) {
      //any action if the request fails
      console.log(error);
    });

```


@[trackingtest]("referral")
