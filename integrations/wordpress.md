# Adding FirstPromoter to Your WordPress Website

FirstPromoter has a dedicated WordPress plugin that makes it easy to add affiliate tracking to your website. The plugin handles click tracking, referral tracking, and sales tracking with built-in support for WooCommerce, MemberPress, Contact Form 7, OptimizePress, custom forms, URL-based email capture, and payment links.

---

## Installing the Plugin

1. Log in to your WordPress admin dashboard.
2. Go to **Plugins > Add New**.
3. Search for **"FirstPromoter"** in the search bar.
4. Click **Install Now**, then **Activate**.

Alternatively, download the plugin directly from the WordPress Plugin Directory and upload it manually via **Plugins > Add New > Upload Plugin**.

---

## Base Configuration

Once activated, go to **FirstPromoter** in the WordPress admin sidebar to configure the plugin.

### Account ID

Your Account ID is required for the tracking script to work on your site.

1. Go to your FirstPromoter dashboard.
2. Navigate to **Settings > Integrations**.
3. Copy your Account ID and paste it into the **Account ID** field in the plugin settings.

### API Key

The API key is required for sale tracking features (WooCommerce sales, MemberPress sales, Contact Form 7).

1. In your FirstPromoter dashboard, go to **Settings > Integrations > Manage API keys**.
2. Copy your API key and paste it into the **API Key** field in the plugin settings.

### Cross-Domain Tracking *(optional)*

If you have multiple domains that need to share tracking data, enter them as a comma-separated list in the **Cross-domain tracking** field.

Example: `example.com, shop.example.com`

This is not needed if you are only using subdomains of the same root domain.

### Force Tracking for Ad-Blockers *(optional)*

Enable **Force tracking even in privacy browsers or with ad-blockers** to use a server-side fallback that keeps referral attribution working when the client-side script is blocked. This applies to all integrations that support server-side tracking.

---

## Integrations

### WooCommerce

The plugin automatically tracks WooCommerce account registrations, checkouts, refunds, and cancellations.

**Signup Tracking**
Enable **Capture email on new account creation** and/or **Capture email on checkout** to record the customer's email when they register or complete a purchase. No API key required.

**Sale Tracking**
Enable **Send sale to FirstPromoter on checkout** to send order data (amount, order ID, coupon codes) to FirstPromoter when an order is marked as processing or completed. Requires an API key.

The plugin also handles:
- **Refunds** — automatically generates negative commissions when an order is refunded.
- **Cancellations** — updates the customer's status in FirstPromoter when an order is cancelled.

---

### MemberPress

Track new member signups and transactions from MemberPress.

**Signup Tracking**
Member registrations are captured automatically when the integration is enabled. No API key required.

**Sale Tracking**
Enable **Track sales/transactions via API** to send transaction data to FirstPromoter. Requires an API key.

Enable **Track recurring payments via API** to track subscription renewals. Requires an API key.

> **Note:** If you are already using FirstPromoter's native Stripe integration to track payments, leave MemberPress sale tracking **disabled** to avoid duplicate sales being recorded.

---

### Contact Form 7

Enable Contact Form 7 tracking to automatically capture form submissions and send them to FirstPromoter. The plugin auto-detects email fields in your forms — any field with "email" in its name is captured.

Requires an API key.

---

### OptimizePress

Enable OptimizePress tracking to capture form submissions from OptimizePress pages. No API key required.

---

### Custom Form Tracking

Track email submissions from any form on your site using CSS selectors — no additional plugin required.

1. Enable **Custom Form Tracking** in the plugin settings.
2. For each form you want to track, enter:
   - **Email input selector** — a CSS selector targeting the email field (e.g. `#email-field`, `input[name="email"]`).
   - **Submit selector** — a CSS selector targeting the submit button or the form element itself (e.g. `#submit-btn`, `form.my-form`).
3. To track multiple forms, check **I have multiple forms to track** and add additional selector pairs.

The plugin uses a MutationObserver to detect dynamically loaded forms, so this works with forms that appear after the initial page load — including popups and AJAX-injected content. A server-side AJAX fallback is also included for cases where ad-blockers interfere with client-side tracking (requires **Force tracking** to be enabled).

---

### URL Email Capture

Capture referrals from thank you pages or confirmation pages where the customer's email is passed as a URL query parameter. Useful when an external checkout or funnel redirects back to your WordPress site with the email in the URL.

1. Enable **URL Email Capture** in the plugin settings.
2. Enter the **Email URL Parameter Key** — the name of the query parameter that contains the email address.
   - Example: for `/thank-you?email=user@example.com`, enter `email`.
3. *(Optional)* Enter the **UID URL Parameter Key** — the name of the query parameter that contains the user ID, if your platform passes one.
   - Example: for `/thank-you?email=user@example.com&uid=12345`, enter `uid`.

No API key required. No plugin dependency — works on any WordPress page.

---

### Payment Links

Automatically append the FirstPromoter tracking ID to payment links on your pages as the `client_reference_id` parameter. This enables FirstPromoter to attribute conversions that happen through direct payment links back to the correct affiliate.

1. Enable **Payment Links** in the plugin settings.
2. Enter the **Payment Link URL Prefix** — links starting with this value will be updated automatically. Defaults to `https://buy.stripe.com/`. Use a comma to separate multiple prefixes.
   - Example for a custom Stripe domain: `https://checkout.mybrand.com/`
   - Example for multiple prefixes: `https://buy.stripe.com/, https://checkout.mybrand.com/`

The plugin uses a MutationObserver to detect payment links added to the page after load (popups, sliders, AJAX content) and updates them as soon as both the link and the FirstPromoter tracking ID are available. No fixed delays, no API key required, no plugin dependency.

> **Note:** This integration is designed for direct payment links placed on your WordPress pages. If you are not embedding `buy.stripe.com` links (or equivalent) directly on your site, this integration is not needed.


### Test Click Tracking

@[trackingtest]("click")

### Test Referral Tracking

@[trackingtest]("referral")