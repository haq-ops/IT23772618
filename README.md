# ITPM — Playwright Test Suite ✅

**Quick overview**

This repository contains a Playwright test suite (TypeScript) that exercises the transliteration site at `https://tamil.changathi.com/`. Tests live in the `tests/` folder and are configured via `playwright.config.ts` (HTML reporter, `./tests` testDir, `trace: 'on-first-retry'`).

---

## 🔧 Prerequisites

- Node.js (16+ recommended)
- Git (optional)

> Dev dependencies include **@playwright/test** (see `package.json`).

---

## ⚙️ Setup

1. Install dependencies

```bash
npm install
```

2. Install Playwright browsers

```bash
npx playwright install
```

(If you prefer scripts, see the **Helpful npm scripts** section below.)

---

## ▶️ Run tests

- Run all tests (headless):

```bash
npx playwright test
```

- Run tests in a specific file:

```bash
npx playwright test tests/example.spec.ts
```

- Run a single test by title (grep):

```bash
npx playwright test -g "Pos_Fun_0001"
```

- Run a test in a specific project (browser):

```bash
npx playwright test --project=chromium
```

- Run tests in headed mode (see them run in a browser):

```bash
npx playwright test --headed
```

---

## 📊 Reports & artifacts

- The config uses the **HTML reporter**. After a run, open the report in your browser:

```bash
npx playwright show-report
```

- A `playwright-report/` directory is created (contains `index.html`).
- Test artifacts and traces (on retry) are recorded under `test-results/` when configured by Playwright.

---

## 🧭 Test structure

- Tests are under `./tests` and use Playwright's recommended pattern:

```ts
import { test, expect } from '@playwright/test';

test('example', async ({ page }) => {
  await page.goto('https://tamil.changathi.com/');
  await page.locator('#transliterateTextarea').fill('example');
  await expect(page.locator('#transliterateTextarea')).toBeVisible();
});
```

- Use `.spec.ts` for test files and add descriptive titles for easier filtering.

---

## ✨ Helpful npm scripts (suggested)

You can add these to `package.json` under `scripts` for convenience:

```json
"scripts": {
  "test": "npx playwright test",
  "test:headed": "npx playwright test --headed",
  "test:report": "npx playwright show-report",
  "install:browsers": "npx playwright install"
}
```

---

## 🐞 Troubleshooting

- If a browser isn't found, run `npx playwright install` again.
- To debug interactively, run a single test with `--headed` and add `console.log` statements or use Playwright's inspector: `npx playwright test --debug`.

---

## 🤝 Contributing

- Add tests under `tests/` and open a PR. Keep tests isolated and deterministic where possible.

---

## 📄 License

- See `package.json` (license: ISC).

---

If you want, I can add convenient npm scripts to `package.json` for you. 💡