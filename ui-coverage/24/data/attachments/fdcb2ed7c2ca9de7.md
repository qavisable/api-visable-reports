# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: ui/tests/user-account/my-account-settings.spec.ts >> My Account settings page >> displays Security section
- Location: ui/tests/user-account/my-account-settings.spec.ts:82:7

# Error details

```
Error: expect(locator).toHaveText(expected) failed

Locator: locator(':nth-child(8) > .font-display-500')
Expected: "Sicherheit"
Timeout: 15000ms
Error: element(s) not found

Call log:
  - Expect "toHaveText" locator(':nth-child(8) > .font-display-500') with timeout 15000ms
  - waiting for locator(':nth-child(8) > .font-display-500')
    - waiting for "https://www.wlw-staging.de/de/user-frontend/settings" navigation to finish...
    - navigated to "https://www.wlw-staging.de/de/user-frontend/settings"

```

```yaml
- banner:
  - link "visable":
    - /url: /de/user-frontend/settings
    - img "visable"
  - button "PA"
  - button "DE"
- heading "Mein Konto" [level=1]
- paragraph: Verwalten Sie Ihre Datenschutz- und Sicherheitseinstellungen für die Dienste von Visable.
- img "europages logo"
- img "werliefertwas logo"
- text: pa
- textbox "Geben Sie Ihren Vornamen ein": purchaser
- textbox "Geben Sie Ihren Nachnamen ein": account
- heading "Über mich" [level=2]
- paragraph: Teilen Sie uns mehr über Ihre Rolle oder Ihren Jobtitel mit, damit wir die Marktplatzfunktion optimal auf Ihre Bedürfnisse anpassen können.
- text: Anrede
- button "Anrede":
  - text: Herr
  - img "arrow-down"
- text: Firmenname
- textbox "Firmenname":
  - /placeholder: Geben Sie den Namen Ihres Unternehmens ein
  - text: Visable
- text: Rolle oder Jobtitel
- textbox "Rolle oder Jobtitel":
  - /placeholder: Geben Sie Ihre Rolle oder Ihren Jobtitel ein
  - text: PO
- text: Abteilung
- textbox "Abteilung":
  - /placeholder: Abteilung eingeben
  - text: Marketing
- button [disabled]
- heading "Meine Unternehmen" [level=2]
- link "toolcraft AG toolcraft AG wlw ep arrow":
  - /url: /de/member-management/00505682-f25b-1ee9-bd91-d2572480b7fb
  - img "toolcraft AG"
  - text: toolcraft AG
  - img "wlw"
  - img "ep"
  - img "arrow"
- text: Es ist ein Fehler aufgetreten, wir können Ihre Unternehmen nicht laden. Um Mitglied eines Unternehmens zu werden, kontaktieren Sie bitte unseren Kundenservice unter
- link "info@wlw.com":
  - /url: mailto:info@wlw.com
- text: . Erstellen Sie Ihr Firmenprofil, um auf 'Wer liefert was (wlw)' gelistet zu werden. Kostenlos
- link "Firma eintragen":
  - /url: /de/supplier-registration
- heading "Sprache" [level=2]
- text: Meine bevorzugte Sprache
- button "English arrow-down":
  - text: English
  - img "arrow-down"
- paragraph: Sie erhalten Kommunikations- und Marketing-E-Mails in Ihrer bevorzugten Sprache.
- heading "Kontoinformationen" [level=2]
- paragraph: Aus technischen Gründen ist eine Änderung der E-Mail-Adresse nicht möglich.
- text: E-Mail-Adresse
- textbox "E-Mail-Adresse" [disabled]:
  - /placeholder: name@firma.com
  - text: test@account.com
- heading "Sicherheit" [level=2]
- text: Passworteinstellungen
- link "Passwort zurücksetzen":
  - /url: /de/user-frontend/password/edit?return_to=%2Fde%2Fuser-frontend%2Fsettings
- heading "Zugriffstoken" [level=3]
- paragraph: Token ermöglichen externen Systemen den Zugriff auf Ihr Konto.
- paragraph: Sie haben keine externen Anwendungen autorisiert.
- button "Dieses Konto löschen"
- img "Visable logo"
- contentinfo:
  - img
  - link "Allgemeinen Geschäftsbedingungen":
    - /url: /de/unternehmen/rechtliche-hinweise/agb
  - link "Allgemeine Bedingungen für die Nutzung":
    - /url: /de/unternehmen/rechtliche-hinweise/nutzungsbedingungen
  - link "Datenschutzbestimmungen":
    - /url: /de/unternehmen/rechtliche-hinweise/datenschutz
  - link "Impressum":
    - /url: /de/unternehmen/rechtliche-hinweise/impressum
```

# Test source

```ts
  60  |   }
  61  | 
  62  |   async expectGivenName(value: string): Promise<void> {
  63  |     await expect(this.page.locator("#givenName[type='text']")).toHaveValue(value);
  64  |   }
  65  | 
  66  |   async expectSurname(value: string): Promise<void> {
  67  |     await expect(this.page.locator("#surname[type='text']")).toHaveValue(value);
  68  |   }
  69  | 
  70  |   async expectPersonalNameFieldsPopulated(): Promise<void> {
  71  |     const givenName = this.page.locator("#givenName[type='text']");
  72  |     const surname = this.page.locator("#surname[type='text']");
  73  |     await expect(givenName).not.toHaveValue('');
  74  |     await expect(surname).not.toHaveValue('');
  75  |   }
  76  | 
  77  |   async expectAboutMeFieldsEnabled(): Promise<void> {
  78  |     await expect(this.page.locator('#salutation')).toBeEnabled();
  79  |     await expect(this.page.locator('#companyName')).toBeEnabled();
  80  |     await expect(this.page.locator('#jobTitle')).toBeEnabled();
  81  |     await expect(this.page.locator('#department')).toBeEnabled();
  82  |   }
  83  | 
  84  |   async expectNotificationsSection(title: string): Promise<void> {
  85  |     await expect(this.notificationsSectionTitle()).toHaveText(title);
  86  |   }
  87  | 
  88  |   async expectMyCompaniesSection(title: string): Promise<void> {
  89  |     await expect(this.myCompaniesSectionTitle()).toHaveText(title);
  90  |     await expect(this.page.locator('a.create-company')).toBeEnabled();
  91  |   }
  92  | 
  93  |   async expectLanguageSection(title: string): Promise<void> {
  94  |     await expect(this.languageSectionTitle()).toHaveText(title);
  95  |     await expect(this.page.locator('button#language')).toBeEnabled();
  96  |   }
  97  | 
  98  |   async expectLanguageSelected(label: string): Promise<void> {
  99  |     await expect(this.page.locator('#language .option')).toHaveText(label);
  100 |   }
  101 | 
  102 |   async scrollToLanguageSection(): Promise<void> {
  103 |     await this.languageDropdownButton().scrollIntoViewIfNeeded();
  104 |     await expect(this.languageDropdownButton()).toBeVisible();
  105 |   }
  106 | 
  107 |   async preferredLanguageLabel(): Promise<string> {
  108 |     const label = await this.languageDropdownButton().locator('.option span').textContent();
  109 |     return (label ?? '').trim();
  110 |   }
  111 | 
  112 |   /** Vis-select dropdown is flaky to open; nudge salutation + retry (Pegasus REG-MA-02). */
  113 |   private async openLanguageDropdown(): Promise<void> {
  114 |     const select = this.languageSelectRoot();
  115 |     const button = this.languageDropdownButton();
  116 |     for (let attempt = 0; attempt < 5; attempt++) {
  117 |       await this.page.locator('button#salutation').click().catch(() => undefined);
  118 |       await this.page.keyboard.press('Escape');
  119 |       await button.scrollIntoViewIfNeeded();
  120 |       await button.click();
  121 |       const opened = await select.evaluate((root) => {
  122 |         const menu = root.querySelector('.dropdown') as HTMLElement | null;
  123 |         return Boolean(menu && getComputedStyle(menu).display === 'flex');
  124 |       });
  125 |       if (opened) return;
  126 |     }
  127 |     throw new Error('Language dropdown did not open after retries');
  128 |   }
  129 | 
  130 |   async selectPreferredLanguage(optionLabel: string): Promise<void> {
  131 |     await this.openLanguageDropdown();
  132 |     await this.languageSelectRoot()
  133 |       .locator('[role="menuitem"]')
  134 |       .filter({ hasText: optionLabel })
  135 |       .click();
  136 |     await expect(this.languageDropdownButton().locator('.option span')).toContainText(
  137 |       optionLabel.startsWith('Deutsch') ? 'Deutsch' : 'English',
  138 |     );
  139 |   }
  140 | 
  141 |   async clickLanguageSave(): Promise<void> {
  142 |     const save = this.languageSaveButton();
  143 |     await expect(save).toBeEnabled({ timeout: 30_000 });
  144 |     await save.click();
  145 |     await expect(save).toBeDisabled({ timeout: 60_000 });
  146 |   }
  147 | 
  148 |   async expectPreferredLanguage(optionLabel: string): Promise<void> {
  149 |     await expect(this.languageDropdownButton().locator('.option span')).toContainText(
  150 |       optionLabel.startsWith('Deutsch') ? 'Deutsch' : 'English',
  151 |     );
  152 |   }
  153 | 
  154 |   async expectAccountInfoSection(title: string): Promise<void> {
  155 |     await expect(this.accountInfoSectionTitle()).toHaveText(title);
  156 |     await expect(this.page.locator('#email')).toBeDisabled();
  157 |   }
  158 | 
  159 |   async expectSecuritySection(title: string): Promise<void> {
> 160 |     await expect(this.securitySectionTitle()).toHaveText(title);
      |                                               ^ Error: expect(locator).toHaveText(expected) failed
  161 |     await expect(this.page.locator('[class*="delete-button"]')).toBeEnabled();
  162 |   }
  163 | 
  164 |   async expectFooterLinks(expected: readonly string[]): Promise<void> {
  165 |     const links = this.page.locator('.content a.link');
  166 |     await expect(links).toHaveCount(expected.length);
  167 |     const texts = await links.allTextContents();
  168 |     expect(texts.map((t) => t.trim())).toEqual([...expected]);
  169 |   }
  170 | 
  171 |   async openNotificationSettings(): Promise<void> {
  172 |     await this.notificationsChangeButton().click();
  173 |   }
  174 | 
  175 |   async expectNotificationSettingsHeading(text: string): Promise<void> {
  176 |     await expect(this.page.locator('h1')).toHaveText(text);
  177 |   }
  178 | 
  179 |   async expectDirectMessageNotificationsOn(): Promise<void> {
  180 |     await expect(this.page.locator('#direct-message-enabled')).toBeChecked();
  181 |     await expect(this.page.locator('#direct-message-email-enabled')).toBeChecked();
  182 |     await expect(this.page.locator('#direct-message-email-enabled')).toBeDisabled();
  183 |   }
  184 | 
  185 |   async expectRfqNotificationsOn(): Promise<void> {
  186 |     await expect(this.page.locator('#request-for-quotes-enabled')).toBeChecked();
  187 |     await expect(this.page.locator('#request-for-quotes-email-enabled')).toBeChecked();
  188 |     await expect(this.page.locator('#request-for-quotes-email-enabled')).toBeDisabled();
  189 |   }
  190 | 
  191 |   async expectSupplierProductNotificationsOn(): Promise<void> {
  192 |     await expect(this.page.locator('#suppliers-enabled')).toBeChecked();
  193 |   }
  194 | 
  195 |   /** Open step only — closed steps stay in DOM without `[open]` (Cypress `dialog.vis-modal:visible`). */
  196 |   private visibleDeleteModal(): Locator {
  197 |     return this.page.locator('dialog.vis-modal').filter({ visible: true }).first();
  198 |   }
  199 | 
  200 |   /** Open delete-account survey (Cypress `clickDeleteAccount`). */
  201 |   async clickDeleteAccount(): Promise<void> {
  202 |     await expect(this.page).toHaveURL(/user-frontend\/settings/);
  203 |     const deleteBtn = this.page.locator('[data-testid="buyer-delete-desktop-action"]');
  204 |     await deleteBtn.scrollIntoViewIfNeeded();
  205 |     await expect(deleteBtn).toBeVisible({ timeout: 30_000 });
  206 |     await expect(deleteBtn).toBeEnabled();
  207 | 
  208 |     const modal = this.visibleDeleteModal();
  209 |     for (let attempt = 0; attempt < 2; attempt++) {
  210 |       await deleteBtn.click();
  211 |       try {
  212 |         await expect(modal).toBeVisible({ timeout: 15_000 });
  213 |         break;
  214 |       } catch (error) {
  215 |         if (attempt === 1) throw error;
  216 |       }
  217 |     }
  218 |     await expect(modal.locator('label:has(input[type="checkbox"])')).not.toHaveCount(0);
  219 |   }
  220 | 
  221 |   /** Survey + confirmation steps inside the visible delete dialog. */
  222 |   async confirmDeleteAccount(): Promise<void> {
  223 |     const modal = this.visibleDeleteModal();
  224 |     await modal.locator('label:has(input[type="checkbox"])').first().click();
  225 |     await modal.locator('button.btn--subtle:not(:disabled)').last().click();
  226 | 
  227 |     const confirmModal = this.visibleDeleteModal();
  228 |     await confirmModal.locator('label').filter({ hasText: /yes|löschen|delete|confirm/i }).click();
  229 |     await confirmModal.locator('button.btn--negative').click();
  230 |   }
  231 | }
  232 | 
```