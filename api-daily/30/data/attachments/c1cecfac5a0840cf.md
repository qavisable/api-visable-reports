# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: api/services/traffic-mesh-backend/ShowroomController/showroom.spec.ts >> honours the requested static page and page size
- Location: api/services/traffic-mesh-backend/ShowroomController/showroom.spec.ts:114:5

# Error details

```
Error: traffic-mesh returned non-JSON (HTTP 502): <html>
<head><title>502 Bad Gateway</title></head>
<body>
<center><h1>502 Bad Gateway</h1></center>
</body>
</html>
<!-- a padding to disable MSIE and Chrome friendly error page -->
<!-- a padd
```

# Test source

```ts
  1   | import { createHash } from 'node:crypto';
  2   | import type { APIRequestContext } from '@playwright/test';
  3   | import type {
  4   |   CrumbsData,
  5   |   SeoCategoryData,
  6   |   ShowroomStaticData,
  7   |   TrafficMeshResponse,
  8   | } from '../models/traffic-mesh';
  9   | 
  10  | type QueryParams = Record<string, string | number | boolean | undefined>;
  11  | 
  12  | /**
  13  |  * Per-request context. `host` is the product host the landing page is resolved for
  14  |  * (wlw needs it together with `Accept-Language`); `language` is sent both as the
  15  |  * `Accept-Language` header and as the query param the controller expects.
  16  |  */
  17  | export type TrafficMeshContext = {
  18  |   host: string;
  19  |   language: string;
  20  | };
  21  | 
  22  | /**
  23  |  * Traffic-mesh showroom HTTP only: returns `{ status, body }`, specs assert.
  24  |  * `dynamictoken` mirrors the Java `GetHeaders` helper (md5 of "VSEO" + 100s bucket).
  25  |  */
  26  | export class TrafficMeshClient {
  27  |   constructor(
  28  |     private readonly request: APIRequestContext,
  29  |     private readonly baseUrl: string,
  30  |   ) {}
  31  | 
  32  |   private headers(ctx: TrafficMeshContext): Record<string, string> {
  33  |     const bucket = Math.floor(Date.now() / 100_000);
  34  |     return {
  35  |       'Content-Type': 'application/json',
  36  |       dynamictoken: createHash('md5').update(`VSEO${bucket}`).digest('hex'),
  37  |       'Accept-Language': ctx.language,
  38  |       'X-Application-Id': 'homepage-frontend',
  39  |       'x-host': ctx.host,
  40  |     };
  41  |   }
  42  | 
  43  |   private async get<T>(
  44  |     path: string,
  45  |     params: QueryParams,
  46  |     ctx: TrafficMeshContext,
  47  |   ): Promise<TrafficMeshResponse<T>> {
  48  |     const query = Object.fromEntries(
  49  |       Object.entries(params)
  50  |         .filter(([, value]) => value !== undefined)
  51  |         .map(([key, value]) => [key, String(value)]),
  52  |     );
  53  |     const response = await this.request.get(`${this.baseUrl}${path}`, {
  54  |       params: query,
  55  |       headers: this.headers(ctx),
  56  |       failOnStatusCode: false,
  57  |     });
  58  |     const text = await response.text();
  59  |     try {
  60  |       return { status: response.status(), body: JSON.parse(text) };
  61  |     } catch {
> 62  |       throw new Error(
      |             ^ Error: traffic-mesh returned non-JSON (HTTP 502): <html>
  63  |         `traffic-mesh returned non-JSON (HTTP ${response.status()}): ${text.slice(0, 200)}`,
  64  |       );
  65  |     }
  66  |   }
  67  | 
  68  |   /**
  69  |    * GET /showroom-cate/data (`seo-category-controller#getSeoCate`).
  70  |    * `category` is the landing-page slug (`elektrotechnik-100038`) and `version`
  71  |    * is mandatory at runtime even though Swagger does not mark it required.
  72  |    */
  73  |   async getSeoCate(
  74  |     params: {
  75  |       category?: string;
  76  |       version?: string;
  77  |       platform: string;
  78  |       site_code?: string;
  79  |       page?: number;
  80  |       per_page?: number;
  81  |       source?: string;
  82  |     },
  83  |     ctx: TrafficMeshContext,
  84  |   ) {
  85  |     return this.get<SeoCategoryData>(
  86  |       '/showroom-cate/data',
  87  |       { ...params, language: ctx.language },
  88  |       ctx,
  89  |     );
  90  |   }
  91  | 
  92  |   /** GET /showroom/v1/crumbs (`Showroom API#getSeoDataCrumbs`). */
  93  |   async getCrumbs(
  94  |     params: {
  95  |       keyword: string;
  96  |       /** Required by the API; optional here so the contract spec can omit it. */
  97  |       siteId?: string;
  98  |       bot?: boolean;
  99  |       tld?: string;
  100 |     },
  101 |     ctx: TrafficMeshContext,
  102 |   ) {
  103 |     return this.get<CrumbsData>(
  104 |       '/showroom/v1/crumbs',
  105 |       { ...params, language: ctx.language },
  106 |       ctx,
  107 |     );
  108 |   }
  109 | 
  110 |   /** GET /showroom/static/data (`Showroom API#getShowroomStaticData`). */
  111 |   async getShowroomStaticData(
  112 |     params: {
  113 |       q?: string;
  114 |       ufsSessionId?: string;
  115 |       platform: string;
  116 |       siteCode?: string;
  117 |       /** Strings allowed so the contract specs can send invalid values. */
  118 |       page?: number | string;
  119 |       perPage?: number | string;
  120 |       urlPath?: string;
  121 |     },
  122 |     ctx: TrafficMeshContext,
  123 |   ) {
  124 |     return this.get<ShowroomStaticData>(
  125 |       '/showroom/static/data',
  126 |       { ...params, language: ctx.language },
  127 |       ctx,
  128 |     );
  129 |   }
  130 | }
  131 | 
```