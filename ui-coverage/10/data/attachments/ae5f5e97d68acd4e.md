# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: ui/tests/user-account/create-account.spec.ts >> user can create an account and confirm email via Mailtrap OTP
- Location: ui/tests/user-account/create-account.spec.ts:40:5

# Error details

```
Error: expect(locator).toBeVisible() failed

Locator: getByRole('menuitem', { name: /^Albania:\s*\+/ })
Expected: visible
Timeout: 15000ms
Error: element(s) not found

Call log:
  - Expect "toBeVisible" getByRole('menuitem', { name: /^Albania:\s*\+/ }) with timeout 15000ms
  - waiting for getByRole('menuitem', { name: /^Albania:\s*\+/ })

```

```yaml
- banner:
  - img
  - button "Get quotes":
    - img
    - text: Get quotes
  - button "Request Hub":
    - img
    - text: Request Hub
  - button "Become a supplier":
    - img
    - text: Become a supplier
  - button:
    - img
  - button "account Sign in":
    - img "account"
    - text: Sign in
  - button "DE"
- main:
  - img
  - heading "Join Europe’s leading B2B marketplace today" [level=1]
  - paragraph: Create a free supplier profile and connect with 1.2 million monthly B2B buyers.
  - list:
    - listitem:
      - img "check"
      - text: Increase your company’s online presence and discoverability
    - listitem:
      - img "check"
      - text: Boost sales from 128,000 daily searches for products and services
    - listitem:
      - img "check"
      - text: Attract new customers with quote requests from 1.2 million monthly B2B buyers
  - heading "First, create your user account" [level=2]
  - paragraph: You will create your company profile in the next step
  - text: Salutation
  - button "Salutation":
    - text: None
    - img "arrow-down"
  - text: First name
  - textbox "First name":
    - /placeholder: ""
  - text: Last name
  - textbox "Last name":
    - /placeholder: ""
  - text: Country code
  - button "Country code":
    - img "arrow-down"
  - text: Phone number (optional)
  - textbox "Phone number (optional)":
    - /placeholder: ""
  - text: Email
  - textbox "Email":
    - /placeholder: username@company.com
  - text: Password
  - textbox "Password":
    - /placeholder: Use at least 8 characters
  - button "Start registration"
  - text: By registering on europages, you accept our
  - link "General Conditions of Use":
    - /url: https://www.europages.co.uk/company/legal-notice/terms-of-use
  - text: . Already registered?
  - link "Log in":
    - /url: /en/login?is_supplier=1&return_to=https%3A%2F%2Fwww.europages-staging.de%3A443%2F.ory%2Fbackend%2Fself-service%2Flogin%2Fbrowser%3Freturn_to%3Dhttps%253A%252F%252Fwww.europages-staging.de%253A443%252Fen%252Fmy-account%252Fnew-company%26language%3Den
  - img
  - paragraph: We’ve had our professional profile on europages for over 20 years. It has greatly contributed, and continues to do so, to new orders, quotations and customer queries for URM.
  - img "Sandhya Singh photo"
  - text: Sandhya Singh Sales & Marketing Development at URM
  - link "Get a premium profile":
    - /url: https://supplier.europages.com/en/rfc
- contentinfo:
  - text: Start with
  - img
  - text: today. Use the full potential of Europe's leading B2B marketplace. Start now for free.
  - button "List my company":
    - img
    - text: List my company
  - button "Unlock our exclusive benefits":
    - img
    - text: Unlock our exclusive benefits
  - button "account Sign in to account":
    - img "account"
    - text: Sign in to account
  - text: "Download our app from the App stores:"
  - link "Download_on_the_App_Store_Badge_US-UK_RGB_blk_4SVG_092917":
    - /url: https://europages.app.link/websiteFooter?$desktop_url=https%3A%2F%2Fapps.apple.com%2Fus%2Fapp%2Feuropages-b2b-sourcing%2Fid6459474480%3Fl%3Den
    - img "Download_on_the_App_Store_Badge_US-UK_RGB_blk_4SVG_092917"
  - link:
    - /url: https://europages.app.link/websiteFooter?$desktop_url=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.visable.ep%26hl%3Den
    - img
  - text: For Buyers
  - list:
    - listitem:
      - link "Request for Quotes":
        - /url: /en/rfq
    - listitem:
      - link "Inside Business":
        - /url: https://www.europages.co.uk/inside-business/start
    - listitem:
      - link "Help Center for Buyers":
        - /url: https://help.europages.com/en/purchaser
    - listitem:
      - link "Buyers Success Stories":
        - /url: https://www.europages.co.uk/inside-business/introduction-to-europages/interviews
  - text: For Suppliers
  - list:
    - listitem:
      - link "List your company":
        - /url: /en/supplier-registration
    - listitem:
      - link "Visable Media Services":
        - /url: https://www.visable.com/en_int/online-marketing
    - listitem:
      - link "Help Center for Suppliers":
        - /url: https://help.europages.com/en/supplier
    - listitem:
      - link "Suppliers Success Stories":
        - /url: https://www.europages.co.uk/inside-business/introduction-to-europages/customer-testimonial
  - text: More about Visable
  - list:
    - listitem:
      - link "Press":
        - /url: https://www.visable.com/en_int/about-us/press
    - listitem:
      - link "Contact":
        - /url: https://www.visable.com/en_int/contact-us
    - listitem:
      - link "Career":
        - /url: https://www.visable.com/en_int/career
    - listitem:
      - link "About us":
        - /url: https://www.visable.com/en_int/about-us
  - text: Trust and partners
  - link "BME Certified with BME Seal of Approval":
    - /url: https://www.bme.de/services/siegel/anbietersuche-europages
    - img "BME"
    - text: Certified with BME Seal of Approval
  - text: This site is protected by reCAPTCHA
  - img
  - text: Partner of the marketplace
  - link "linkedin":
    - /url: https://www.linkedin.com/company/europages
    - img "linkedin"
  - link:
    - /url: https://www.facebook.com/europages
    - img
  - link:
    - /url: https://www.youtube.com/user/europagesvideo
    - img
  - link:
    - /url: https://x.com/europages
    - img
  - list:
    - listitem:
      - link "General Conditions of Use":
        - /url: https://www.europages.co.uk/company/legal-notice/terms-of-use
    - listitem:
      - link "Privacy policy":
        - /url: https://www.europages.co.uk/company/legal-notice/privacy-policy-1
    - listitem:
      - link "Privacy notice":
        - /url: https://www.europages.co.uk/company/legal-notice/privacy-notice
    - listitem:
      - link "Cookie policy":
        - /url: https://www.europages.co.uk/company/legal-notice/cookie-policy
```

# Test source

```ts
  1  | /**
  2  |  * `expect` whose every matcher call becomes an Allure step carrying its expected
  3  |  * value, so the report lists assertions instead of bare `Expect "toBe"` lines.
  4  |  * API assertions are synchronous; web-first assertions (`expect(locator)`,
  5  |  * `expect(page)`, `expect(response).toBeOK()`) return promises and need the
  6  |  * async step API. `expect.poll` stays untouched for the same reason.
  7  |  */
  8  | import { expect as baseExpect } from '@playwright/test';
  9  | import { step as asyncStep } from 'allure-js-commons';
  10 | import { step } from 'allure-js-commons/sync';
  11 | 
  12 | const MAX_PREVIEW = 80;
  13 | 
  14 | function preview(value: unknown): string {
  15 |   if (typeof value === 'string') {
  16 |     const text = value.length > MAX_PREVIEW ? `${value.slice(0, MAX_PREVIEW)}…` : value;
  17 |     return JSON.stringify(text);
  18 |   }
  19 |   if (
  20 |     value === null ||
  21 |     typeof value === 'number' ||
  22 |     typeof value === 'boolean' ||
  23 |     typeof value === 'undefined'
  24 |   ) {
  25 |     return String(value);
  26 |   }
  27 |   if (value instanceof RegExp) return String(value);
  28 |   try {
  29 |     const json = JSON.stringify(value);
  30 |     if (json !== undefined) return json.length > MAX_PREVIEW ? `${json.slice(0, MAX_PREVIEW)}…` : json;
  31 |   } catch {
  32 |     // circular structures fall through to the type preview
  33 |   }
  34 |   if (Array.isArray(value)) return `Array(${value.length})`;
  35 |   if (value instanceof Map) return `Map(${value.size})`;
  36 |   if (value instanceof Set) return `Set(${value.size})`;
  37 |   if (typeof value === 'object') {
  38 |     return (value as object).constructor?.name ?? 'object';
  39 |   }
  40 |   return String(value);
  41 | }
  42 | 
  43 | type MatcherFunction = (...args: unknown[]) => unknown;
  44 | type Matchers = Record<PropertyKey, unknown>;
  45 | 
  46 | /** Web-first assertions poll and return a promise; locators, pages and API responses use them. */
  47 | function isAsyncTarget(actual: unknown): boolean {
  48 |   if (!actual || typeof actual !== 'object') return false;
  49 |   const target = actual as Record<string, unknown>;
  50 |   if (typeof target._frame === 'object' && target._frame !== null) return true;
  51 |   if (typeof target.goto === 'function' && typeof target.context === 'function') return true;
  52 |   return typeof target.status === 'function' && typeof target.headersArray === 'function';
  53 | }
  54 | 
  55 | function withSteps(matchers: Matchers, negated: boolean, actual: unknown): Matchers {
  56 |   return new Proxy(matchers, {
  57 |     get(target, prop, receiver) {
  58 |       const value = Reflect.get(target, prop, receiver);
  59 |       if (typeof prop !== 'string') return value;
  60 |       if (prop === 'not') return withSteps(value as Matchers, !negated, actual);
  61 |       if (typeof value !== 'function') return value;
  62 |       return (...args: unknown[]) => {
  63 |         const title = `assert ${negated ? 'not ' : ''}${prop}(${args.map(preview).join(', ')})`;
> 64 |         const matcher = () => (value as MatcherFunction).apply(target, args);
     |                                                          ^ Error: expect(locator).toBeVisible() failed
  65 |         if (isAsyncTarget(actual)) return asyncStep(title, matcher);
  66 |         return step(title, matcher);
  67 |       };
  68 |     },
  69 |   });
  70 | }
  71 | 
  72 | export const expect = new Proxy(baseExpect, {
  73 |   apply(target, _thisArg, args: [unknown, ...unknown[]]) {
  74 |     return withSteps(
  75 |       (target as unknown as (...a: unknown[]) => Matchers)(...args),
  76 |       false,
  77 |       args[0],
  78 |     );
  79 |   },
  80 |   get(target, prop, receiver) {
  81 |     const value = Reflect.get(target, prop, receiver);
  82 |     if (prop === 'soft') {
  83 |       return (actual: unknown, message?: string) =>
  84 |         withSteps(
  85 |           (value as (a: unknown, m?: string) => Matchers)(actual, message),
  86 |           false,
  87 |           actual,
  88 |         );
  89 |     }
  90 |     if (prop === 'poll') {
  91 |       return (...args: unknown[]) => (value as (...a: unknown[]) => unknown)(...args);
  92 |     }
  93 |     return typeof value === 'function' ? value.bind(target) : value;
  94 |   },
  95 | }) as unknown as typeof baseExpect;
  96 | 
```