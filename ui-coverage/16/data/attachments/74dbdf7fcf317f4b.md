# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: ui/tests/product/product-detail.spec.ts >> shows related products
- Location: ui/tests/product/product-detail.spec.ts:38:5

# Error details

```
Error: expect(received).toBeGreaterThanOrEqual(expected)

Expected: >= 1
Received:    0

Call Log:
- Timeout 30000ms exceeded while waiting on the predicate
```

# Page snapshot

```yaml
- generic [ref=f1e3]:
  - generic [ref=f1e6]:
    - banner [ref=f1e8]:
      - generic [ref=f1e11]:
        - generic [ref=f1e12] [cursor=pointer]
        - generic [ref=f1e20]:
          - generic [ref=f1e21]:
            - textbox "Search form" [ref=f1e22]:
              - /placeholder: ""
            - generic:
              - generic:
                - generic:
                  - generic: rotationsdämpfer
                  - generic: magnesiumclorit
                  - generic: eeg geräte
                  - generic: rotationsdämpfer
          - button "Search" [ref=f1e23] [cursor=pointer]
        - button "Angebotsanfrage" [ref=f1e29] [cursor=pointer]
        - button "Anfragenportal" [ref=f1e40] [cursor=pointer]
        - button "Werden Sie Lieferant" [ref=f1e52] [cursor=pointer]
        - button [ref=f1e63] [cursor=pointer]
        - button "account Anmelden" [ref=f1e70] [cursor=pointer]:
          - img "account" [ref=f1e72]
          - generic [ref=f1e74]: Anmelden
        - button "DE" [ref=f1e77] [cursor=pointer]
    - generic [ref=f1e83]:
      - heading "Es ist ein Fehler aufgetreten" [level=1] [ref=f1e84]
      - paragraph [ref=f1e85]: Ein interner Fehler ist aufgetreten oder Ihre Internetverbindung ist instabil.
      - paragraph [ref=f1e86]:
        - text: Bitte nutzen Sie die Suche oder klicken Sie
        - link "hier" [ref=f1e87] [cursor=pointer]:
          - /url: /
        - text: ", um die Startseite aufzurufen"
  - contentinfo [ref=f1e89]:
    - generic [ref=f1e92]:
      - generic [ref=f1e93]: Newsletter für Einkäufer abonnieren und informiert bleiben.
      - generic [ref=f1e99]:
        - textbox "Ihre E‑Mail‑Adresse" [ref=f1e100]
        - link "Abonnieren" [ref=f1e101] [cursor=pointer]:
          - /url: https://mail.wlw.com/newsletter-registrierung?email=&visable_lead_source=Buyer_wlw_subscribe_bar
    - generic [ref=f1e102]:
      - generic [ref=f1e103]:
        - generic [ref=f1e104]:
          - generic [ref=f1e105]:
            - generic [ref=f1e106]:
              - generic [ref=f1e107]: Beginnen Sie mit
              - generic [ref=f1e113]: Heute.
            - generic [ref=f1e114]: Nutzen Sie das volle Potenzial des führenden B2B-Marktplatzes der DACH-Region. Starten Sie jetzt kostenlos.
          - generic [ref=f1e115]:
            - button "Firma eintragen" [ref=f1e117] [cursor=pointer]
            - button "Schalten Sie unsere exklusiven Vorteile frei" [ref=f1e125] [cursor=pointer]
            - button "account Anmelden" [ref=f1e130] [cursor=pointer]:
              - img "account" [ref=f1e131]
              - generic [ref=f1e133]: Anmelden
          - generic [ref=f1e134]:
            - generic [ref=f1e135]: "Laden Sie unsere App aus den App-Stores herunter:"
            - generic [ref=f1e136]:
              - link [ref=f1e137] [cursor=pointer]:
                - /url: https://wlw.app.link/websiteFooter?$desktop_url=https%3A%2F%2Fapps.apple.com%2Fde%2Fapp%2Fwer-liefert-was-wlw%2Fid1531873496%3Fl%3Dde
              - link [ref=f1e147] [cursor=pointer]:
                - /url: https://wlw.app.link/websiteFooter?$desktop_url=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.visable.wlw%26hl%3Dde
        - generic [ref=f1e161]:
          - generic [ref=f1e163]:
            - generic [ref=f1e164]: Für Einkäufer
            - list [ref=f1e169]:
              - listitem [ref=f1e170]:
                - link "Angebotsanfrage" [ref=f1e171] [cursor=pointer]:
                  - /url: /de/rfq
              - listitem [ref=f1e172]:
                - link "Inside Business" [ref=f1e173] [cursor=pointer]:
                  - /url: https://www.wlw.de/de/inside-business/start
              - listitem [ref=f1e174]:
                - link "Hilfe-Center für Einkäufer" [ref=f1e175] [cursor=pointer]:
                  - /url: https://hilfe.wlw.de/einkaeufer
          - generic [ref=f1e177]:
            - generic [ref=f1e178]: Für Anbieter
            - list [ref=f1e183]:
              - listitem [ref=f1e184]:
                - link "Firma eintragen" [ref=f1e185] [cursor=pointer]:
                  - /url: /de/supplier-registration
              - listitem [ref=f1e186]:
                - link "Visable Online Marketing" [ref=f1e187] [cursor=pointer]:
                  - /url: https://www.visable.com/de_de/online-marketing
              - listitem [ref=f1e188]:
                - link "Hilfe-Center für Anbieter" [ref=f1e189] [cursor=pointer]:
                  - /url: https://hilfe.wlw.de/de/anbieter
              - listitem [ref=f1e190]:
                - link "Anbieter Erfolgsgeschichten" [ref=f1e191] [cursor=pointer]:
                  - /url: https://www.wlw.de/de/inside-business/fuer-lieferanten/erfolgsstorys
          - generic [ref=f1e193]:
            - generic [ref=f1e194]: Mehr über Visable
            - list [ref=f1e199]:
              - listitem [ref=f1e200]:
                - link "Presse" [ref=f1e201] [cursor=pointer]:
                  - /url: https://www.visable.com/de_de/ueber-uns/presse
              - listitem [ref=f1e202]:
                - link "Kontakt" [ref=f1e203] [cursor=pointer]:
                  - /url: https://www.visable.com/de_de/kontakt
              - listitem [ref=f1e204]:
                - link "Karriere" [ref=f1e205] [cursor=pointer]:
                  - /url: https://www.visable.com/de_de/karriere
              - listitem [ref=f1e206]:
                - link "Über uns" [ref=f1e207] [cursor=pointer]:
                  - /url: https://www.visable.com/de_de/ueber-uns
          - generic [ref=f1e209]:
            - generic [ref=f1e210]: Vertrauen und Partner
            - generic [ref=f1e215]:
              - link "BME Zertifiziert mit dem BME-Gütesiegel" [ref=f1e217] [cursor=pointer]:
                - /url: https://www.bme.de/services/siegel/Anbietersuche-wlw
                - img "BME" [ref=f1e218]
                - generic [ref=f1e219]: Zertifiziert mit dem BME-Gütesiegel
              - generic [ref=f1e220]: Diese Website ist durch reCAPTCHA geschützt
              - generic [ref=f1e224]: Partner des Marktplatzes
      - generic [ref=f1e229]:
        - generic [ref=f1e230]:
          - link "linkedin" [ref=f1e231] [cursor=pointer]:
            - /url: https://www.linkedin.com/company/wer-liefert-was-gmbh
            - img "linkedin" [ref=f1e232]
          - link [ref=f1e234] [cursor=pointer]:
            - /url: https://www.facebook.com/werliefertwas
          - link [ref=f1e237] [cursor=pointer]:
            - /url: https://www.youtube.com/user/werliefertwasde
          - link [ref=f1e240] [cursor=pointer]:
            - /url: https://x.com/wlw_vonvisable
        - list [ref=f1e243]:
          - listitem [ref=f1e244]:
            - link "Allgemeine Geschäftsbedingungen" [ref=f1e245] [cursor=pointer]:
              - /url: /de/unternehmen/rechtliche-hinweise/agb
          - listitem [ref=f1e246]:
            - link "Allgemeine Bedingungen für die Nutzung" [ref=f1e247] [cursor=pointer]:
              - /url: /de/unternehmen/rechtliche-hinweise/nutzungsbedingungen
          - listitem [ref=f1e248]:
            - link "Datenschutzbestimmungen" [ref=f1e249] [cursor=pointer]:
              - /url: /de/unternehmen/rechtliche-hinweise/datenschutz
          - listitem [ref=f1e250]:
            - link "Impressum" [ref=f1e251] [cursor=pointer]:
              - /url: /de/unternehmen/rechtliche-hinweise/impressum
```

# Test source

```ts
  1  | /**
  2  |  * Regression: product detail page (PDP) — port of Cypress `wlw-pdp-regression` and
  3  |  * `ep-pdp-regression`.
  4  |  */
  5  | import { expect, test } from '../../../fixtures';
  6  | import { buyerPages } from '../../../config/buyer-pages';
  7  | import { ProductDetailPage } from '../../pages/product/product-detail.page';
  8  | 
  9  | let pdp: ProductDetailPage;
  10 | 
  11 | test.beforeEach(async ({ publicPage, product }) => {
  12 |   pdp = new ProductDetailPage(publicPage, product);
  13 |   await pdp.open(buyerPages(product).productDetail);
  14 | });
  15 | 
  16 | test('loads the PDP URL with the product path', {
  17 |   tag: ['@smoke', '@regression', '@wlw', '@ep'],
  18 | }, async ({ publicPage, product }) => {
  19 |   await expect(publicPage).toHaveURL(buyerPages(product).productDetailUrlSegment);
  20 | });
  21 | 
  22 | test('shows the product title', { tag: ['@smoke', '@regression', '@wlw', '@ep'] }, async () => {
  23 |   await expect(pdp.seoTitle()).toHaveText(/\S/);
  24 | });
  25 | 
  26 | test('shows the about section', { tag: ['@regression', '@wlw', '@ep'] }, async () => {
  27 |   await expect(pdp.aboutHeading()).toBeVisible();
  28 | });
  29 | 
  30 | test('shows a contact button', { tag: ['@regression', '@wlw', '@ep'] }, async () => {
  31 |   await expect(pdp.contactButton()).toBeVisible();
  32 | });
  33 | 
  34 | test('shows breadcrumbs', { tag: ['@smoke', '@regression', '@wlw', '@ep'] }, async () => {
  35 |   await expect(pdp.breadcrumbs()).toBeVisible();
  36 | });
  37 | 
  38 | test('shows related products', { tag: ['@regression', '@wlw', '@ep'] }, async () => {
  39 |   await expect
  40 |     .poll(() => pdp.relatedProductNames().count(), { timeout: 30_000 })
> 41 |     .toBeGreaterThanOrEqual(1);
     |      ^ Error: expect(received).toBeGreaterThanOrEqual(expected)
  42 | });
  43 | 
  44 | test('shows the product description', { tag: ['@regression', '@wlw'] }, async () => {
  45 |   await expect(pdp.description()).toBeAttached();
  46 | });
  47 | 
  48 | test('shows the product image', { tag: ['@regression', '@wlw'] }, async () => {
  49 |   await expect(pdp.productImage()).toBeAttached();
  50 | });
  51 | 
  52 | test.skip('opens the contact flow when clicking the contact button', {
  53 |   tag: ['@regression', '@wlw', '@ep'],
  54 | }, async () => {
  55 |   // Staging gap: clicking contact loads the ContactSupplierForm remote module but no
  56 |   // dialog, form, or textarea mounts on wlw or ep.
  57 | });
  58 | 
```