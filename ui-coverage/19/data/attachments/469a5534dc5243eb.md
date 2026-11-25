# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: ui/tests/user-account/my-account-settings.spec.ts >> My Account settings page >> displays Language section
- Location: ui/tests/user-account/my-account-settings.spec.ts:61:7

# Error details

```
Error: Kratos login failed (HTTP 401)
```

# Test source

```ts
  1  | import type { APIRequestContext } from '@playwright/test';
  2  | import type { ProductFamily } from '../../../../config/platforms';
  3  | import {
  4  |   loadPlatformEnv,
  5  |   personaCredentials,
  6  |   type Persona,
  7  | } from '../../../../config/load-platform-env';
  8  | import { KratosClient } from '../clients/kratos-client';
  9  | 
  10 | /** Password login via Kratos API (session cookies on `apiRequest`). Spec or UI flow syncs to browser. */
  11 | export async function loginPersonaViaApi(
  12 |   apiRequest: APIRequestContext,
  13 |   product: ProductFamily,
  14 |   persona: Persona,
  15 | ): Promise<void> {
  16 |   const { email, password } = personaCredentials(product, persona);
  17 |   await loginWithCredentialsViaApi(apiRequest, product, email, password);
  18 | }
  19 | 
  20 | export async function loginWithCredentialsViaApi(
  21 |   apiRequest: APIRequestContext,
  22 |   product: ProductFamily,
  23 |   email: string,
  24 |   password: string,
  25 | ): Promise<void> {
  26 |   const kratos = new KratosClient(apiRequest, loadPlatformEnv(product).baseUrl);
  27 |   const session = await kratos.loginWithPassword(email, password);
  28 |   if (session.status !== 200) {
> 29 |     throw new Error(`Kratos login failed (HTTP ${session.status})`);
     |           ^ Error: Kratos login failed (HTTP 401)
  30 |   }
  31 | }
  32 | 
```