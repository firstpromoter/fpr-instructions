# Adding FirstPromoter to your custom website using Javascript

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

To track referrals, you'll need to make a request to FirstPromoter to capture the lead. This can mainly be done by calling the "fpr" JavaScript function defined in the main tracking script and inserting the email of the user/lead/customer: `fpr("referral", {email: "user-email"})`

If you can't use the email for privacy reasons, you can use the "uid" instead.
`fpr("referral”,{uid:"user-id-in-database"})`

***NB: The scripts should be placed or called underneath the main tracking script.***

~~~markdown [g2:JavaScript]

1. Find the section in your code where you can get access to the email/uid of the current user. Preferably the sign up page, opt-in form or checkout page.
2. Write some code to capture the email and pass it to the `fpr` function like this:  `fpr("referral", {email: "actual@email.com"})`.

If you are having a simple form on your website, you can capture the email from the input field and make the request when the submit button is pressed. This code can be put in the `&lt;head&gt;` section of your website right below the main tracking script which you added from above. Below is an example of what your code may look like.

```html
&lt;script&gt;
  function sendLeadToFP(){
      const emailInput = document.querySelector(&apos;input[type=&quot;email&quot;]&apos;)
      const submitButton = document.querySelector(&quot;button[type=&apos;submit&apos;]&quot;);

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
```
~~~


~~~markdown [g2:Capture from Url]

If you&apos;re using a checkout plugin or service that appends the email to the thank-you page like `https://website.com/thank-you?email=user@email.com`, you can grab the email from the url and pass it to the `fpr` function as shown below. This can be added directly into the `&lt;head&gt;` section of your website.

```html
&lt;script&gt;
  function getParam(param){
    return new URLSearchParams(window.location.search).get(param);
  }
  fpr(&quot;referral&quot;,{email: getParam(&quot;email&quot;)})
&lt;/script&gt;
```

***NB: If you&apos;re performing a redirect after calling the function, please double-check it, as redirection blocks any ongoing requests in most browsers (in this case it might be better have a delay or put the script on the redirected page instead).***

~~~

~~~markdown [g2:Vue]

For Vue you can make the call on a success callback function or even on a click handler.

1. Find the section in your code where you can get access to the email/uid of the current user. Preferably the sign up page, opt-in form or checkout page.
2. Capture the email and pass it to the `fpr` function like this:  `fpr("referral", {email: "actual@email.com"})`.
3. Below is an example of what the code may look like. 

***NB: The scripts below is just a guide. Please do not copy and paste it directly into your code as it will not work.***

```html {noCopy}
&lt;template&gt;
  &lt;form @submit.prevent=&quot;submitForm&quot;&gt;
    &lt;input v-model=&quot;data.firstName&quot; name=&quot;firstName&quot; type=&quot;text&quot;/&gt;
    &lt;input v-model=&quot;data.lastName&quot; name=&quot;lastName&quot; type=&quot;text&quot;/&gt;
    &lt;input v-model=&quot;data.email&quot; name=&quot;email&quot; type=&quot;email&quot;/&gt;
    &lt;input v-model=&quot;data.password&quot; name=&quot;password&quot; type=&quot;password&quot;/&gt;
    &lt;button type=&quot;submit&quot;&gt;Send Email&lt;/button&gt;
  &lt;/form&gt;
&lt;/template&gt;

&lt;script setup &gt;
  import {reactive} from &quot;vue&quot;;
  import axios from &quot;axios&quot;;

  const data = reactive({
    firstName:&quot;&quot;,
    lastName:&quot;&quot;,
    email:&quot;&quot;,
    password:&quot;&quot;,
  });

  function sendEmailToFirstPromoter(){
     window.fpr(&quot;referral&quot;,{email: data.email})
  }

  function submitForm(){
    axios.post(&quot;/backend-service/register&quot;,{data}).then((response)=&gt;{
      console.log(response.data); // Log the response data

      //Make request to FirstPromoter
      sendEmailToFirstPromoter();

    }).catch (error) {
      console.error(&quot;Registration failed:&quot;, error);
      // Handle error (e.g., show error message to user)
    }  
  }
&lt;/script&gt;
```
~~~

~~~markdown [g2:React]

In React you can make the call on a success callback function or even on a click handler.

1. Find the section in your code where you can get access to the email/uid of the current user. Preferably the sign up page, opt-in form or checkout page.
2. Capture the email and pass it to the `fpr` function like this:  `fpr("referral", {email: "actual@email.com"})`.
3. Below is an example of what the code may look like. 

```js {noCopy}
import React, { useState } from &apos;react&apos;;
import axios from &apos;axios&apos;;

function RegistrationForm() {
  const [formData, setFormData] = useState({
    firstName: &apos;&apos;,
    lastName: &apos;&apos;,
    email: &apos;&apos;,
    password: &apos;&apos;
  });

  const handleInputChange = (e) =&gt; {
    const { name, value } = e.target;
    setFormData({
      ...formData,
      [name]: value
    });
  };

  const sendEmailToFirstPromoter = () =&gt; {
    // Assuming window.fpr is defined and is a function to send email to first promoter
    window.fpr(&apos;referral&apos;, { email: formData.email });
  };

  const submitForm = async (e) =&gt; {
    e.preventDefault();

    try {
      const response = await axios.post(&apos;/backend-service/register&apos;, formData);
      console.log(response.data); // Log the response data
      sendEmailToFirstPromoter(); // Send email to first promoter after successful registration
    } catch (error) {
      console.error(&apos;Registration failed:&apos;, error);
      // Handle error (e.g., show error message to user)
    }
  };

  return (
    &lt;form onSubmit={submitForm}&gt;
      &lt;input
        type=&quot;text&quot;
        name=&quot;firstName&quot;
        value={formData.firstName}
        onChange={handleInputChange}
        placeholder=&quot;First Name&quot;
      /&gt;
      &lt;input
        type=&quot;text&quot;
        name=&quot;lastName&quot;
        value={formData.lastName}
        onChange={handleInputChange}
        placeholder=&quot;Last Name&quot;
      /&gt;
      &lt;input
        type=&quot;email&quot;
        name=&quot;email&quot;
        value={formData.email}
        onChange={handleInputChange}
        placeholder=&quot;Email&quot;
      /&gt;
      &lt;input
        type=&quot;password&quot;
        name=&quot;password&quot;
        value={formData.password}
        onChange={handleInputChange}
        placeholder=&quot;Password&quot;
      /&gt;
      &lt;button type=&quot;submit&quot;&gt;Register&lt;/button&gt;
    &lt;/form&gt;
  );
}

export default RegistrationForm;
```

~~~

~~~markdown [g2:Angular]
In Angular you can make the call on a success callback function or even on a click handler.

1. Find the section in your code where you can get access to the email/uid of the current user. Preferably the sign up page, opt-in form or checkout page.
2. Capture the email and pass it to the `fpr` function like this:  `fpr("referral", {email: "actual@email.com"})`.
3. Below is an example of what the code might look like assuming you have a component representing a sign-up form (SignUpComponent).

### Template File
```html {noCopy}
<form (ngSubmit)="onSubmit()">
  <label for="firstName">First Name:</label>
  <input type="text" id="firstName" name="firstName" [(ngModel)]="formData.firstName" required>

  <label for="lastName">Last Name:</label>
  <input type="text" id="lastName" name="lastName" [(ngModel)]="formData.lastName" required>

  <label for="email">Email:</label>
  <input type="email" id="email" name="email" [(ngModel)]="formData.email" required>

  <label for="password">Password:</label>
  <input type="password" id="password" name="password" [(ngModel)]="formData.password" required>

  <button type="submit">Register</button>
</form>

```

### Component

```js {noCopy}

import { Component } from '@angular/core';
import axios from 'axios'; // Import Axios for HTTP requests (if using)

@Component({
  selector: 'app-sign-up',
  templateUrl: './sign-up.component.html',
  styleUrls: ['./sign-up.component.css']
})
export class SignUpComponent {
  formData = {
    firstName: '',
    lastName: '',
    email: '',
    password: ''
  };

  constructor() {}

  onSubmit(): void {
    axios.post('/backend-service/register', this.formData)
      .then(response => {
        console.log('Registration successful:', response.data);
        const userEmail = this.formData.email;
        this.sendReferralEmail(userEmail);
      })
      .catch(error => {
        console.error('Registration failed:', error);
      });
  }

  sendReferralEmail(email: string): void {
    //here we call the fpr function
    window.fpr('referral', { email });
  }
}

```
~~~

@[trackingtest]("referral")
