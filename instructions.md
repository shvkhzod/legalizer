# INSTRUCTIONS: AI Charity Compliance Checker (Scraper-Only)

## 1. Project Overview

**Project:** "Charity Compliance Checker"
**Goal:** A modern, minimalistic website that performs an automated compliance scan. The user provides a URL, a web scraper analyzes the site, gives it to the AI, and AI generates report.
**Tech Stack:** SvelteKit, TypeScript, Plain CSS (no external libraries), Anthropic Claude.
**Design Style:** Minimalistic, modern, "Apple-inspired," authentic, fast, perfect Type System and Layouts.
**Core Font:** Inter (to be self-hosted or imported).

**New Workflow:**
1.  **Home Page (`/`):** User enters their website URL.
2.  **Scan Page (`/scan`):**
    * The page shows a loading spinner.
    * The `+page.server.ts` file for this page runs.
    * It calls the **web scraping method** (`scrapeWebsite`).
    * It passes the scraper's results to the **report engine** which is AI (`generateReport`).
    * The AI returns the final `ComplianceReport`.
    * The Svelte page receives the report data and displays it using the `ReportDisplay` component.

---

## 2. Design System & Global Styles

Create a global stylesheet in `/src/app.css`.

### 2.1. Font Import
Import the "Inter" font (weights 400, 600, 700) at the top of `app.css`.

### 2.2. CSS Variables (Root)

```css
:root {
  /* Fonts */
  --font-primary: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
    Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;

  /* Colors (Apple Palette) */
  --color-bg-primary: #ffffff;
  --color-bg-secondary: #f5f5f7;
  --color-text-primary: #1d1d1f;
  --color-text-secondary: #6e6e73;
  --color-accent: #007aff;
  --color-border: #d2d2d7;

  /* Status Colors */
  --status-good: #34c759;
  --status-warning: #ff9500;
  --status-threat: #ff3b30;
  --status-info: #5ac8fa;

  /* Sizing & Spacing */
  --spacing-xs: 0.25rem;
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;
  --spacing-lg: 1.5rem;
  --spacing-xl: 2.5rem;
  --spacing-xxl: 4rem;

  /* UI Elements */
  --border-radius: 8px;
  --card-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  --transition-fast: all 0.2s cubic-bezier(0.25, 0.8, 0.25, 1);

  /* Layout */
  --container-width: 980px;
} 


* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
html,
body {
  font-family: var(--font-primary);
  background-color: var(--color-bg-primary);
  color: var(--color-text-primary);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
main {
  width: 100%;
  max-width: var(--container-width);
  margin: 0 auto;
  padding: var(--spacing-xxl) var(--spacing-md);
}
/* Perfect Type System */
h1 {
  font-size: 3rem;
  font-weight: 700;
  line-height: 1.1;
  letter-spacing: -0.02em;
  margin-bottom: var(--spacing-md);
}
h2 {
  font-size: 2.25rem;
  font-weight: 600;
  line-height: 1.2;
  letter-spacing: -0.015em;
  margin-bottom: var(--spacing-lg);
  margin-top: var(--spacing-xl);
}
h3 {
  font-size: 1.5rem;
  font-weight: 600;
  line-height: 1.3;
  margin-bottom: var(--spacing-sm);
  margin-top: var(--spacing-lg);
}
p,
li {
  font-size: 1rem;
  line-height: 1.6;
  color: var(--color-text-secondary);
  margin-bottom: var(--spacing-md);
}
a {
  color: var(--color-accent);
  text-decoration: none;
  transition: var(--transition-fast);
}
a:hover {
  opacity: 0.8;
}

/* Shared UI Components */
.button {
  display: inline-block;
  font-size: 1rem;
  font-weight: 600;
  padding: var(--spacing-md) var(--spacing-lg);
  border-radius: var(--border-radius);
  background-color: var(--color-accent);
  color: var(--color-bg-primary);
  border: none;
  cursor: pointer;
  transition: var(--transition-fast);
}
.button:hover {
  transform: scale(1.02);
  opacity: 0.9;
}
.input {
  width: 100%;
  font-size: 1.1rem;
  padding: var(--spacing-md);
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius);
  background-color: var(--color-bg-secondary);
  color: var(--color-text-primary);
  transition: var(--transition-fast);
}
.input:focus {
  outline: none;
  border-color: var(--color-accent);
  box-shadow: 0 0 0 2px rgba(0, 122, 255, 0.2);
}

This instruction set removes the manual questionnaire (/check) entirely.

The new workflow is a purely automated, two-step process:

Homepage (/): User enters a URL.

Scan Page (/scan): The server scrapes the website, generates a report from only the scraped data, and displays it.

All internal policy checks (like MFA, DBS, etc.) that cannot be verified by scraping a public website are removed. The report will only contain checks that can be objectively proven by the scraper.

Markdown

# INSTRUCTIONS: AI Charity Compliance Checker (Scraper-Only)

## 1. Project Overview

**Project:** "Charity Compliance Checker"
**Goal:** A modern, minimalistic website that performs an automated compliance scan. The user provides a URL, a web scraper analyzes the site, and a report is generated based *only* on the publicly available data.
**Tech Stack:** SvelteKit, TypeScript, Plain CSS (no external libraries).
**Design Style:** Minimalistic, "Apple-inspired," authentic, fast.
**Core Font:** Inter (to be self-hosted or imported).

**New Workflow:**
1.  **Home Page (`/`):** User enters their website URL.
2.  **Scan Page (`/scan`):**
    * The page shows a loading spinner.
    * The `+page.server.ts` file for this page runs.
    * It calls the **web scraping method** (`scrapeWebsite`).
    * It passes the scraper's results to the **report engine** (`generateReport`).
    * The server function returns the final `ComplianceReport`.
    * The Svelte page receives the report data and displays it using the `ReportDisplay` component.

---

## 2. Design System & Global Styles

Create a global stylesheet in `/src/app.css`.

### 2.1. Font Import
Import the "Inter" font (weights 400, 600, 700) at the top of `app.css`.

### 2.2. CSS Variables (Root)
```css
:root {
  /* Fonts */
  --font-primary: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
    Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;

  /* Colors (Apple Palette) */
  --color-bg-primary: #ffffff;
  --color-bg-secondary: #f5f5f7;
  --color-text-primary: #1d1d1f;
  --color-text-secondary: #6e6e73;
  --color-accent: #007aff;
  --color-border: #d2d2d7;

  /* Status Colors */
  --status-good: #34c759;
  --status-warning: #ff9500;
  --status-threat: #ff3b30;
  --status-info: #5ac8fa;

  /* Sizing & Spacing */
  --spacing-xs: 0.25rem;
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;
  --spacing-lg: 1.5rem;
  --spacing-xl: 2.5rem;
  --spacing-xxl: 4rem;

  /* UI Elements */
  --border-radius: 8px;
  --card-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  --transition-fast: all 0.2s cubic-bezier(0.25, 0.8, 0.25, 1);

  /* Layout */
  --container-width: 980px;
}
2.3. Global Resets & Typography
In app.css, apply base styles.

CSS

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
html,
body {
  font-family: var(--font-primary);
  background-color: var(--color-bg-primary);
  color: var(--color-text-primary);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
main {
  width: 100%;
  max-width: var(--container-width);
  margin: 0 auto;
  padding: var(--spacing-xxl) var(--spacing-md);
}
/* Perfect Type System */
h1 {
  font-size: 3rem;
  font-weight: 700;
  line-height: 1.1;
  letter-spacing: -0.02em;
  margin-bottom: var(--spacing-md);
}
h2 {
  font-size: 2.25rem;
  font-weight: 600;
  line-height: 1.2;
  letter-spacing: -0.015em;
  margin-bottom: var(--spacing-lg);
  margin-top: var(--spacing-xl);
}
h3 {
  font-size: 1.5rem;
  font-weight: 600;
  line-height: 1.3;
  margin-bottom: var(--spacing-sm);
  margin-top: var(--spacing-lg);
}
p,
li {
  font-size: 1rem;
  line-height: 1.6;
  color: var(--color-text-secondary);
  margin-bottom: var(--spacing-md);
}
a {
  color: var(--color-accent);
  text-decoration: none;
  transition: var(--transition-fast);
}
a:hover {
  opacity: 0.8;
}

/* Shared UI Components */
.button {
  display: inline-block;
  font-size: 1rem;
  font-weight: 600;
  padding: var(--spacing-md) var(--spacing-lg);
  border-radius: var(--border-radius);
  background-color: var(--color-accent);
  color: var(--color-bg-primary);
  border: none;
  cursor: pointer;
  transition: var(--transition-fast);
}
.button:hover {
  transform: scale(1.02);
  opacity: 0.9;
}
.input {
  width: 100%;
  font-size: 1.1rem;
  padding: var(--spacing-md);
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius);
  background-color: var(--color-bg-secondary);
  color: var(--color-text-primary);
  transition: var(--transition-fast);
}
.input:focus {
  outline: none;
  border-color: var(--color-accent);
  box-shadow: 0 0 0 2px rgba(0, 122, 255, 0.2);
}
3. Project Structure
Create the following file structure. (Note: /check route and checkStore are removed).

/src
  /lib
    /components
      /Header.svelte
      /Footer.svelte
      /ScanInputForm.svelte
      /LoadingSpinner.svelte
      /ReportDisplay.svelte
      /ReportCard.svelte
    /utils
      /types.ts
      /scraper.ts           <-- The web scraping method
      /reportEngine.ts      <-- Generates report from scraped data
  /routes
    /+page.svelte           <-- Landing page
    /scan
      /+page.server.ts      <-- Runs scraper + report engine
      /+page.svelte         <-- Shows loading & displays report
    /+layout.svelte
  /app.css
  /app.html



  This instruction set removes the manual questionnaire (/check) entirely.

The new workflow is a purely automated, two-step process:

Homepage (/): User enters a URL.

Scan Page (/scan): The server scrapes the website, generates a report from only the scraped data, and displays it.

All internal policy checks (like MFA, DBS, etc.) that cannot be verified by scraping a public website are removed. The report will only contain checks that can be objectively proven by the scraper.

Markdown

# INSTRUCTIONS: AI Charity Compliance Checker (Scraper-Only)

## 1. Project Overview

**Project:** "Charity Compliance Checker"
**Goal:** A modern, minimalistic website that performs an automated compliance scan. The user provides a URL, a web scraper analyzes the site, and a report is generated based *only* on the publicly available data.
**Tech Stack:** SvelteKit, TypeScript, Plain CSS (no external libraries).
**Design Style:** Minimalistic, "Apple-inspired," authentic, fast.
**Core Font:** Inter (to be self-hosted or imported).

**New Workflow:**
1.  **Home Page (`/`):** User enters their website URL.
2.  **Scan Page (`/scan`):**
    * The page shows a loading spinner.
    * The `+page.server.ts` file for this page runs.
    * It calls the **web scraping method** (`scrapeWebsite`).
    * It passes the scraper's results to the **report engine** (`generateReport`).
    * The server function returns the final `ComplianceReport`.
    * The Svelte page receives the report data and displays it using the `ReportDisplay` component.

---

## 2. Design System & Global Styles

Create a global stylesheet in `/src/app.css`.

### 2.1. Font Import
Import the "Inter" font (weights 400, 600, 700) at the top of `app.css`.

### 2.2. CSS Variables (Root)
```css
:root {
  /* Fonts */
  --font-primary: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
    Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;

  /* Colors (Apple Palette) */
  --color-bg-primary: #ffffff;
  --color-bg-secondary: #f5f5f7;
  --color-text-primary: #1d1d1f;
  --color-text-secondary: #6e6e73;
  --color-accent: #007aff;
  --color-border: #d2d2d7;

  /* Status Colors */
  --status-good: #34c759;
  --status-warning: #ff9500;
  --status-threat: #ff3b30;
  --status-info: #5ac8fa;

  /* Sizing & Spacing */
  --spacing-xs: 0.25rem;
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;
  --spacing-lg: 1.5rem;
  --spacing-xl: 2.5rem;
  --spacing-xxl: 4rem;

  /* UI Elements */
  --border-radius: 8px;
  --card-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  --transition-fast: all 0.2s cubic-bezier(0.25, 0.8, 0.25, 1);

  /* Layout */
  --container-width: 980px;
}
2.3. Global Resets & Typography
In app.css, apply base styles.

CSS

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
html,
body {
  font-family: var(--font-primary);
  background-color: var(--color-bg-primary);
  color: var(--color-text-primary);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
main {
  width: 100%;
  max-width: var(--container-width);
  margin: 0 auto;
  padding: var(--spacing-xxl) var(--spacing-md);
}
/* Perfect Type System */
h1 {
  font-size: 3rem;
  font-weight: 700;
  line-height: 1.1;
  letter-spacing: -0.02em;
  margin-bottom: var(--spacing-md);
}
h2 {
  font-size: 2.25rem;
  font-weight: 600;
  line-height: 1.2;
  letter-spacing: -0.015em;
  margin-bottom: var(--spacing-lg);
  margin-top: var(--spacing-xl);
}
h3 {
  font-size: 1.5rem;
  font-weight: 600;
  line-height: 1.3;
  margin-bottom: var(--spacing-sm);
  margin-top: var(--spacing-lg);
}
p,
li {
  font-size: 1rem;
  line-height: 1.6;
  color: var(--color-text-secondary);
  margin-bottom: var(--spacing-md);
}
a {
  color: var(--color-accent);
  text-decoration: none;
  transition: var(--transition-fast);
}
a:hover {
  opacity: 0.8;
}

/* Shared UI Components */
.button {
  display: inline-block;
  font-size: 1rem;
  font-weight: 600;
  padding: var(--spacing-md) var(--spacing-lg);
  border-radius: var(--border-radius);
  background-color: var(--color-accent);
  color: var(--color-bg-primary);
  border: none;
  cursor: pointer;
  transition: var(--transition-fast);
}
.button:hover {
  transform: scale(1.02);
  opacity: 0.9;
}
.input {
  width: 100%;
  font-size: 1.1rem;
  padding: var(--spacing-md);
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius);
  background-color: var(--color-bg-secondary);
  color: var(--color-text-primary);
  transition: var(--transition-fast);
}
.input:focus {
  outline: none;
  border-color: var(--color-accent);
  box-shadow: 0 0 0 2px rgba(0, 122, 255, 0.2);
}
3. Project Structure
Create the following file structure. (Note: /check route and checkStore are removed).

/src
  /lib
    /components
      /Header.svelte
      /Footer.svelte
      /ScanInputForm.svelte
      /LoadingSpinner.svelte
      /ReportDisplay.svelte
      /ReportCard.svelte
    /utils
      /types.ts
      /scraper.ts           <-- The web scraping method
      /reportEngine.ts      <-- Generates report from scraped data
  /routes
    /+page.svelte           <-- Landing page
    /scan
      /+page.server.ts      <-- Runs scraper + report engine
      /+page.svelte         <-- Shows loading & displays report
    /+layout.svelte
  /app.css
  /app.html
4. TypeScript Definitions
Create /src/lib/utils/types.ts. This is simplified.

TypeScript

// /src/lib/utils/types.ts

// --- Part 1: Report Output (The Goal) ---

export type ComplianceStatus =
  | 'Compliant'
  | 'Warning'
  | 'Non-Compliant'
  | 'Info';

export interface ComplianceCheck {
  id: string;
  title: string;
  status: ComplianceStatus;
  summary: string; // A 1-sentence summary of the finding.
  recommendation: string; // Actionable advice.
}

export interface ComplianceReport {
  scannedUrl: string;
  scanDate: string;
  overallStatus: ComplianceStatus;
  overallScore: number; // 0-100
  summary: {
    goodPoints: string[];
    warnings: string[];
    threats: string[];
  };
  checks: {
    websitePolicies: ComplianceCheck[];
    security: ComplianceCheck[];
    memberData: ComplianceCheck[]; // Will only contain 'Copyright'
    marketing: ComplianceCheck[]; // Will only contain 'PECR'
    payments: ComplianceCheck[]; // Will only contain 'PCI-DSS'
  };
}

// --- Part 2: Scraper Output (The Source) ---

/**
 * The data structure returned by the scraper.
 * This is the *only* input for the report engine.
 */
export interface ScrapedData {
  scannedUrl: string;
  usesSSL: boolean;
  foundPages: {
    privacy: string | null; // URL of the page if found
    cookie: string | null;
    safeguarding: string | null;
  };
  foundCopyright: boolean;
  paymentType: 'third-party' | 'self-hosted' | 'none';
  pecrCheck: 'opt-in' | 'opt-out' | 'unknown';
  foundGiftAid: boolean;
  privacyPolicyChecks: { // Checks *within* the privacy policy
    mentionsDSAR: boolean;
    mentionsDataProcessors: boolean;
  };
}


// --- 1. Security ---
  if (data.usesSSL) {
    checks.security.push({
      id: 'ssl',
      title: 'SSL Certificate (HTTPS)',
      status: 'Compliant',
      summary: 'Site is served over HTTPS with a valid certificate.',
      recommendation: 'No action needed. Keep your certificate renewed.',
    });
    summary.goodPoints.push('Website is secure (HTTPS).');
    score += 20;
  } else {
    checks.security.push({
      id: 'ssl',
      title: 'SSL Certificate (HTTPS)',
      status: 'Non-Compliant',
      summary: 'Site is not served over HTTPS.',
      recommendation:
        'This is a high risk. All sites must use HTTPS. Install a free Let\'s Encrypt certificate.',
    });
    summary.threats.push('Site is not secure (no HTTPS).');
  }

  // --- 2. Website Policies ---
  if (data.foundPages.privacy) {
    checks.websitePolicies.push({
      id: 'privacy_policy',
      title: 'Privacy Policy',
      status: 'Compliant',
      summary: `A Privacy Policy page was found at ${data.foundPages.privacy}.`,
      recommendation: 'Good. Ensure it is linked in your website footer.',
    });
    summary.goodPoints.push('Has a Privacy Policy.');
    score += 15;
  } else {
    checks.websitePolicies.push({
      id: 'privacy_policy',
      title: 'Privacy Policy',
      status: 'Non-Compliant',
      summary: 'A "Privacy Policy" page could not be found.',
      recommendation:
        'This is a major GDPR risk. You must create and display a Privacy Policy immediately.',
    });
    summary.threats.push('No Privacy Policy page found.');
  }

  if (data.foundPages.cookie) {
    checks.websitePolicies.push({
      id: 'cookie_policy',
      title: 'Cookie Policy',
      status: 'Compliant',
      summary: `A Cookie Policy page was found at ${data.foundPages.cookie}.`,
      recommendation: 'Good. Ensure it is clear and up-to-date.',
    });
    summary.goodPoints.push('Has a Cookie Policy.');
    score += 5;
  } else {
    checks.websitePolicies.push({
      id: 'cookie_policy',
      title: 'Cookie Policy',
      status: 'Warning',
      summary: 'A dedicated "Cookie Policy" page could not be found.',
      recommendation:
        'This is recommended. You can also include cookie information in your Privacy Policy.',
    });
    summary.warnings.push('No dedicated Cookie Policy page.');
  }
  // (Add logic for Safeguarding policy...)

  // --- 3. Marketing (PECR) ---
  if (data.pecrCheck === 'opt-in') {
    checks.marketing.push({
      id: 'pecr_opt_in',
      title: 'Email Marketing (PECR)',
      status: 'Compliant',
      summary: 'Newsletter signup form appears to be "opt-in".',
      recommendation: 'This is correct. Do not use pre-ticked boxes.',
    });
    summary.goodPoints.push('PECR-compliant email marketing.');
    score += 10;
  } else if (data.pecrCheck === 'opt-out') {
    checks.marketing.push({
      id: 'pecr_opt_in',
      title: 'Email Marketing (PECR)',
      status: 'Non-compliant',
      summary: 'Newsletter signup form appears to be "opt-out" (pre-ticked).',
      recommendation: 'This is not compliant with PECR/GDPR. All marketing consent must be explicit and opt-in (unchecked).',
    });
    summary.threats.push('Email marketing form is not opt-in.');
  } else {
    checks.marketing.push({
      id: 'pecr_opt_in',
      title: 'Email Marketing (PECR)',
      status: 'Info',
      summary: 'Could not determine email marketing consent type.',
      recommendation: 'Ensure any email signup forms use an unchecked, opt-in box.',
    });
  }
  
  // --- 4. Privacy Policy Contents ---
  if(data.foundPages.privacy) {
    if (data.privacyPolicyChecks.mentionsDSAR) {
      checks.websitePolicies.push({
        id: 'dsar',
        title: 'DSAR Process (in Privacy Policy)',
        status: 'Compliant',
        summary: 'Your Privacy Policy mentions DSARs.',
        recommendation: 'Good. Ensure the process is clear.',
      });
      summary.goodPoints.push('Privacy Policy mentions DSARs.');
      score += 10;
    } else {
       checks.websitePolicies.push({
        id: 'dsar',
        title: 'DSAR Process (in Privacy Policy)',
        status: 'Warning',
        summary: 'Your Privacy Policy does not seem to mention "DSAR" or "Subject Access Request".',
        recommendation: 'You must update your policy to explain how a user can request a copy of their data.',
      });
      summary.warnings.push('Privacy Policy missing DSAR info.');
    }
  }

  // --- 5. Payments (PCI DSS & Gift Aid) ---
  if (data.paymentType === 'third-party') {
    checks.payments.push({
      id: 'pci_dss',
      title: 'e-Payments (PCI DSS)',
      status: 'Compliant',
      summary: 'Site uses a third-party processor (e.g., Stripe, PayPal).',
      recommendation:
        'This is the best practice as it offloads PCI DSS compliance to the payment provider.',
    });
    summary.goodPoints.push('Uses secure 3rd-party payments.');
    score += 10;
  }
  // (Add logic for Gift Aid, Copyright...)


  // --- Final Report Object ---
  const finalScore = Math.max(0, Math.min(100, score)); // Clamp score 0-100
  const report: ComplianceReport = {
    scannedUrl: data.scannedUrl,
    scanDate: new Date().toISOString(),
    overallScore: finalScore,
    overallStatus:
      finalScore > 85
        ? 'Compliant'
        : finalScore > 60
        ? 'Warning'
        : 'Non-Compliant',
    summary,
    checks,
  };