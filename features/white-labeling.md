# White Labeling

TinkerBunker supports white labeling, allowing partners to brand the platform with their own logo, company name, and custom domain. This creates a seamless branded experience for their institutes and students.

---

## Overview

White labeling enables partners to present TinkerBunker as their own platform:

| Feature              | Description                                          |
| -------------------- | ---------------------------------------------------- |
| Custom Logo          | Partner's logo on login page and header              |
| Company Name         | Partner's brand name on login page                   |
| Custom Domain        | Partner-specific URL for platform access             |
| Branded Login        | Login page shows partner branding via domain detect  |
| Header Branding      | Partner logo displayed alongside or instead of TinkerBunker logo |

---

## How It Works

### Domain Detection

When a user visits the TinkerBunker login page, the system detects the domain and loads the appropriate branding:

```
User visits partner-domain.com
         │
         ▼
Frontend sends: GET /api/v1/partners/by-url?url=partner-domain.com
         │
         ▼
Backend looks up partner by partner_url
         │
    ┌────┴────┐
    ▼         ▼
  Found     Not Found
    │         │
    ▼         ▼
  Show       Show default
  partner    TinkerBunker
  branding   branding
```

### Known TinkerBunker Domains

The following domains show the default TinkerBunker branding:

- `ai.tinkerbunker.com`
- `test.tinkerbunker.com`
- Other designated TinkerBunker domains

Any other domain triggers the partner lookup for white-label branding.

---

## Setup Requirements

### Subscription Plan

White labeling features are controlled by the partner's subscription plan:

| Feature              | Subscription Field       | Description                        |
| -------------------- | ------------------------ | ---------------------------------- |
| Logo Upload          | `allow_logo_upload`      | Partner can upload a custom logo   |
| Custom Domain        | `allow_custom_domain`    | Partner can set a custom URL       |

{% hint style="info" %}
Not all subscription plans include white labeling. The Sales agent or Admin Publisher must assign a plan that includes these features.
{% endhint %}

### Assigning White Label Features

1. **Sales or Admin Publisher** navigates to the partner's detail page
2. Clicks **Assign Subscription Plan**
3. Selects a plan with white-label features enabled
4. Configures:

| Field                  | Description                              |
| ---------------------- | ---------------------------------------- |
| `partner_url`          | Custom domain URL                        |
| `partner_company_name` | Brand name to display                    |
| `partner_logo`         | Logo image URL                           |

5. Confirms the assignment

---

## Branding Locations

### Login Page

The login page dynamically shows partner branding:

- **Partner Logo** — Displayed prominently on the login form
- **Company Name** — Shown below or alongside the logo
- **Default** — If no partner matches the domain, TinkerBunker branding is shown

![Partner Login Page](../.gitbook/assets/partner-login-page.png)

### Application Header

After login, the header reflects the branding:

- **TinkerBunker domains** — Show the TinkerBunker logo
- **Partner domains** — Show the partner logo alongside or instead of the TinkerBunker logo
- The partner logo is sourced from `user.partner_logo` in the auth state

### Mobile Menu

The mobile navigation menu also displays the partner logo when available, ensuring consistent branding across devices.

---

## Partner Logo Management

### Uploading a Logo

Partners with `allow_logo_upload` in their subscription can manage their own logo:

1. Navigate to **Profile** > **Personal Info**
2. Click on the logo upload area
3. Select an image file
4. The logo is uploaded and saved
5. All platform pages update to show the new logo

### Logo Requirements

| Requirement | Specification                    |
| ----------- | -------------------------------- |
| Format      | PNG, JPG, SVG                    |
| Size        | Recommended 200x200px minimum    |
| Aspect      | Square or landscape orientation  |

{% hint style="warning" %}
Logo upload is gated by the `canUploadLogo()` check, which verifies the partner's subscription includes `allow_logo_upload`. Partners without this feature will not see the upload option.
{% endhint %}

---

## Custom Domain Setup

### DNS Configuration

To use a custom domain, the partner must configure their DNS:

1. Add a CNAME record pointing to TinkerBunker's server
2. Notify the Sales agent or Admin Publisher
3. The `partner_url` is set in the subscription assignment
4. SSL certificate is provisioned (if applicable)

### Domain Matching

The system matches domains using the `GET /partners/by-url?url=...` endpoint:

1. Frontend extracts the current domain from `window.location`
2. Sends the domain to the API
3. API performs an exact match on `partner_url`
4. Returns partner branding data (logo, company name)

---

## Auth State Integration

After login, white-label data is stored in the user's auth state:

| Auth Field           | Description                              |
| -------------------- | ---------------------------------------- |
| `partner_logo`       | URL of the partner's logo                |
| `allow_logo_upload`  | Whether the user can change the logo     |

This data is used throughout the application to render consistent branding.

---

## Hierarchy and Inheritance

```
Partner (branded with custom logo and domain)
  ├── Institute A (sees partner's branding)
  │     ├── Teachers (see partner's branding)
  │     └── Students (see partner's branding)
  └── Sub-Partner (can have its own branding)
        └── Institute B (sees sub-partner's branding)
```

Each level in the hierarchy can have its own branding, with sub-partners maintaining separate white-label configurations.

---

## Troubleshooting

| Issue                          | Solution                                          |
| ------------------------------ | ------------------------------------------------- |
| Partner logo not showing       | Verify `allow_logo_upload` is in the subscription |
| Login page shows default brand | Check DNS CNAME and `partner_url` configuration   |
| Logo upload option missing     | Subscription plan may not include logo upload     |
| Wrong logo displayed           | Clear browser cache; verify `partner_logo` field  |
| Custom domain not resolving    | Check DNS propagation (can take up to 48 hours)   |

---

## Next Steps

- [Role Access Matrix](role-access-matrix.md) — See which roles have white-labeling access
- [Managing Partners](../sales/managing-partners.md) — Configure partner branding
- [Billing](billing.md) — Subscription plans that enable white labeling
