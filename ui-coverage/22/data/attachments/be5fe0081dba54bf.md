# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: ui/tests/search/ai-product-search-regression.spec.ts >> AI product search regression >> SERP interactions >> shows pagination when present
- Location: ui/tests/search/ai-product-search-regression.spec.ts:65:9

# Error details

```
Error: expect(locator).toBeVisible() failed

Locator: getByTestId('product-search-results').first()
Expected: visible
Timeout: 60000ms
Error: element(s) not found

Call log:
  - Expect "toBeVisible" getByTestId('product-search-results').first() with timeout 60000ms
  - waiting for getByTestId('product-search-results').first()
    - waiting for "https://www.wlw-staging.de/de/products?q=cnc" navigation to finish...
    - navigated to "https://www.wlw-staging.de/de/products?q=cnc"

```

```yaml
- heading "503 Service Temporarily Unavailable" [level=1]
```

# Test source

```ts
  1   | /** AI product search P-SERP — page load, reasoning panel, filters, cards. */
  2   | import { expect, type Locator, type Page } from '@playwright/test';
  3   | import { aiProductSearchDefaults } from '../../../config/ai-product-search';
  4   | import { urlFor, type ProductFamily } from '../../../config/platforms';
  5   | import {
  6   |   dismissSerpOverlays,
  7   |   dismissDeliveryModalIfPresent,
  8   |   expectValidLink,
  9   |   productCardCompanyName,
  10  |   serpHeaderSearchInput,
  11  |   serpHeaderSearchSubmit,
  12  |   setAiSearchExperimentCookie,
  13  |   visibleSerpReasoningToggle,
  14  | } from './ai-search-helpers';
  15  | import { SerpFilters } from './serp-filters';
  16  | 
  17  | const MOQ_PATTERN = /^\s*\d+[\d.,]*\s*[a-zA-ZäöüßÄÖÜ]+/;
  18  | 
  19  | export class AiProductSearchPage {
  20  |   private readonly filters: SerpFilters;
  21  | 
  22  |   constructor(
  23  |     private readonly page: Page,
  24  |     private readonly product: ProductFamily,
  25  |   ) {
  26  |     this.filters = new SerpFilters(page);
  27  |   }
  28  | 
  29  |   cards(): Locator {
  30  |     return this.page.getByTestId('product');
  31  |   }
  32  | 
  33  |   async open(query: string = aiProductSearchDefaults(this.product).query): Promise<void> {
  34  |     const { pagePath } = aiProductSearchDefaults(this.product);
  35  |     await setAiSearchExperimentCookie(this.page.context(), urlFor(this.product));
  36  |     // The SERP keeps long-lived requests open, so `load` can hang for a minute-plus;
  37  |     // `waitForReady` asserts the real readiness signals instead.
  38  |     await this.page.goto(`${pagePath}?q=${encodeURIComponent(query)}`, {
  39  |       waitUntil: 'domcontentloaded',
  40  |     });
  41  |     await this.waitForReady();
  42  |   }
  43  | 
  44  |   async waitForReady(): Promise<void> {
  45  |     await expect(this.page.getByTestId('loader')).toHaveCount(0, { timeout: 90_000 });
> 46  |     await expect(this.page.getByTestId('product-search-results').first()).toBeVisible({
      |                                                                           ^ Error: expect(locator).toBeVisible() failed
  47  |       timeout: 60_000,
  48  |     });
  49  |     await dismissDeliveryModalIfPresent(this.page);
  50  |     // The EP AI backend slows down under parallel workers; give the first card more room.
  51  |     await expect(this.cards().first()).toBeVisible({ timeout: 150_000 });
  52  |     await dismissSerpOverlays(this.page);
  53  |   }
  54  | 
  55  |   async expectPageStructure(): Promise<void> {
  56  |     await expect(this.page.getByTestId('header').first()).toBeAttached();
  57  |     await expect(serpHeaderSearchInput(this.page)).toBeAttached();
  58  |     await expect(this.page.getByTestId('product-search-results').first()).toBeVisible();
  59  |   }
  60  | 
  61  |   /** The page owns its URL context, so specs do not read env paths or hosts. */
  62  |   async expectPageUrl(): Promise<void> {
  63  |     const { pagePath } = aiProductSearchDefaults(this.product);
  64  |     await expect(this.page).toHaveURL(new RegExp(pagePath));
  65  |     expect(new URL(this.page.url()).host).toBe(new URL(urlFor(this.product)).host);
  66  |   }
  67  | 
  68  |   async expectResults(minCount = 1): Promise<void> {
  69  |     await expect(this.cards().nth(minCount - 1)).toBeAttached({ timeout: 30_000 });
  70  |   }
  71  | 
  72  |   async expectCardVisible(index = 0): Promise<void> {
  73  |     await expect(this.cards().nth(index)).toBeVisible();
  74  |   }
  75  | 
  76  |   async expectUrlContainsQuery(query: string): Promise<void> {
  77  |     await expect.poll(() => new URL(this.page.url()).searchParams.get('q')).toBe(query);
  78  |   }
  79  | 
  80  |   async searchFromHeader(query: string): Promise<void> {
  81  |     await serpHeaderSearchInput(this.page).fill(query);
  82  |     await dismissSerpOverlays(this.page);
  83  |     await serpHeaderSearchSubmit(this.page).click();
  84  |     await expect(this.page).toHaveURL(/\/products/);
  85  |     await this.waitForReady();
  86  |     await this.expectUrlContainsQuery(query);
  87  |   }
  88  | 
  89  |   async expectTabsVisible(): Promise<void> {
  90  |     await expect(this.page.getByTestId('companies-tab')).toBeVisible();
  91  |     await expect(this.page.getByTestId('products-tab')).toBeVisible();
  92  |   }
  93  | 
  94  |   async switchToCompanyTab(): Promise<void> {
  95  |     await dismissSerpOverlays(this.page);
  96  |     await this.page.getByTestId('companies-tab').click({ force: true });
  97  |     await expect(this.page).not.toHaveURL(/\/products/);
  98  |     await expect(this.page.getByTestId('loader')).toHaveCount(0, { timeout: 90_000 });
  99  |     await expect(this.page.getByTestId('company').first()).toBeVisible({ timeout: 90_000 });
  100 |   }
  101 | 
  102 |   async expectBreadcrumbs(): Promise<void> {
  103 |     const breadcrumbs = this.page.getByTestId('breadcrumbs').first();
  104 |     await expect(breadcrumbs).toBeVisible();
  105 |     await expect(breadcrumbs.locator('a').first()).toBeAttached();
  106 |   }
  107 | 
  108 |   async expectPaginationIfPresent(): Promise<void> {
  109 |     const pagination = this.page.getByTestId('pagination').first();
  110 |     if ((await pagination.count()) === 0) {
  111 |       return;
  112 |     }
  113 |     await expect(pagination).toBeVisible();
  114 |   }
  115 | 
  116 |   async expectReasoningPanelExpandedIfPresent(): Promise<boolean> {
  117 |     const toggle = await visibleSerpReasoningToggle(this.page);
  118 |     if (!toggle) {
  119 |       return false;
  120 |     }
  121 |     await dismissSerpOverlays(this.page);
  122 |     await this.openReasoningPanel(toggle);
  123 |     return true;
  124 |   }
  125 | 
  126 |   async expectReasoningPanelCycleIfPresent(): Promise<boolean> {
  127 |     const toggle = await visibleSerpReasoningToggle(this.page);
  128 |     if (!toggle) {
  129 |       return false;
  130 |     }
  131 |     await dismissSerpOverlays(this.page);
  132 |     await this.openReasoningPanel(toggle);
  133 | 
  134 |     const chevron = this.reasoningChevron(toggle);
  135 |     await toggle.click({ force: true });
  136 |     await expect(chevron).not.toHaveClass(/is-open/, { timeout: 15_000 });
  137 |     await expect(toggle).toBeVisible();
  138 |     return true;
  139 |   }
  140 | 
  141 |   async expectProductFilters(): Promise<void> {
  142 |     await this.filters.expectProductFilters();
  143 |   }
  144 | 
  145 |   async expectSortingVisible(): Promise<void> {
  146 |     await this.filters.expectSortingVisible();
```