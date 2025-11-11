# Charity Compliance Checker

A modern, minimalistic website that performs automated compliance scans for charity websites. Built with SvelteKit, TypeScript, and Anthropic Claude AI.

## Features

- **Security Checks**: SSL/HTTPS verification
- **Policy Detection**: Automatically finds Privacy, Cookie, and Safeguarding policies
- **GDPR Compliance**: Checks for DSAR processes and data processor disclosures
- **Marketing Compliance**: Verifies PECR compliance for email marketing
- **Payment Security**: Checks PCI DSS compliance for payment processing
- **AI-Enhanced Reports**: Uses Anthropic Claude to provide detailed insights

## Tech Stack

- **Framework**: SvelteKit
- **Language**: TypeScript
- **Styling**: Plain CSS (no external libraries)
- **Font**: Inter (Google Fonts)
- **AI**: Anthropic Claude API

## Project Structure

```
/src
  /lib
    /components      # Reusable Svelte components
    /utils          # Utility functions (scraper, report engine, types)
  /routes
    /               # Home page
    /scan           # Scan results page
  app.css           # Global styles
  app.html          # HTML template
```

## Getting Started

### Prerequisites

- Node.js 18+
- npm or pnpm
- Anthropic API key (optional, for AI-enhanced reports)

### Installation

1. Clone the repository:
```bash
git clone <your-repo-url>
cd legalizer
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file (optional for AI features):
```bash
cp .env.example .env
```

4. Add your Anthropic API key to `.env`:
```
ANTHROPIC_API_KEY=your_api_key_here
```

### Development

Start the development server:

```bash
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

### Building for Production

Build the application:

```bash
npm run build
```

Preview the production build:

```bash
npm run preview
```

## How It Works

1. **User Input**: User enters a charity website URL on the home page
2. **Web Scraping**: The server scrapes the website to gather publicly available data:
   - SSL/HTTPS status
   - Policy pages (Privacy, Cookie, Safeguarding)
   - Copyright notices
   - Payment processing type
   - Email marketing forms (PECR compliance)
3. **Report Generation**: The scraped data is analyzed to generate a compliance report
4. **AI Enhancement** (optional): If an API key is provided, Claude AI enhances the report with additional insights
5. **Display**: The comprehensive report is displayed with scores, status badges, and actionable recommendations

## Compliance Checks

### Security
- SSL Certificate (HTTPS)

### Website Policies
- Privacy Policy
- Cookie Policy
- Safeguarding Policy
- DSAR Process disclosure
- Data Processors disclosure

### Marketing
- PECR compliance (opt-in email marketing)

### Payments
- PCI DSS compliance
- Gift Aid mentions

### Member Data
- Copyright notice

## Design Principles

- **Minimalistic**: Clean, Apple-inspired design
- **Fast**: Optimized performance with SvelteKit
- **Authentic**: Professional, trustworthy aesthetic
- **Accessible**: Clear typography and color contrast
- **Responsive**: Works on all device sizes

## Configuration

The design system uses CSS variables defined in `src/app.css`:

- Colors: Apple-inspired palette
- Spacing: Consistent scale (xs to xxl)
- Typography: Inter font family
- Status colors: Green (compliant), Orange (warning), Red (non-compliant), Blue (info)

## Limitations

- Only scans publicly available information
- Cannot verify internal policies (MFA, DBS checks, etc.)
- Basic heuristics for some checks (e.g., PECR detection)
- Requires valid URLs with accessible pages

## Future Enhancements

- Support for deeper crawling
- More sophisticated HTML parsing
- Additional compliance frameworks
- Export reports as PDF
- Historical scan comparison
- Multi-language support

## License

All rights reserved.

## Disclaimer

This tool provides automated guidance only. Always consult with a qualified legal professional for compliance advice.
