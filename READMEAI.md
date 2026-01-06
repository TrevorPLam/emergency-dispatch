You are a senior full-stack engineer building a production-ready local service website template in a GitHub repo (developed in GitHub Codespaces).

GOAL
Build “Archetype 4 — Emergency / Dispatch (call-first)” as a reusable, modern, high-converting marketing template for businesses like emergency plumbing, HVAC emergency, towing, garage door emergency.

Primary conversion: CALL NOW (immediate). Secondary: SMS/Text (optional), then short “request callback” form (last resort).

STACK (REQUIRED)
- Next.js (App Router)
- TypeScript
- Tailwind CSS
No CMS. No database. Single config file for all content + behavior.

MARKETING + COMPLIANCE STANDARDS FOR THIS ARCHETYPE (NON-NEGOTIABLE)
A) Call-first UX (dominant action)
- Every page must prioritize one-tap calling on mobile.
- The page should not distract with multiple competing CTAs; CALL NOW is dominant.
This aligns with mobile landing page guidance: clear, uncluttered, quick to act. :contentReference[oaicite:3]{index=3}

B) Trust + legitimacy above the fold
- Emergency businesses must show trust signals immediately:
  - license/insured placeholders (TODO:INPUT)
  - reviews snippet
  - service area clarity
Google emphasizes representing business info accurately/consistently for local trust. :contentReference[oaicite:4]{index=4}

C) Pricing expectations for honesty (reduce panic friction)
- Must include a “Pricing Expectations” section:
  - trip/diagnostic fee (if applicable) as TODO:INPUT
  - transparent “typical range” phrasing (no invented numbers)

D) Ad/LSA compatibility and call tracking
- Provide call-tracking ready hooks (config-driven):
  - optional “tracking number” display vs underlying tel link
  - call click events tracked
Google emphasizes effective mobile landing pages and measuring conversion quality. :contentReference[oaicite:5]{index=5}

OUTPUT CONTRACT (ANTI-TRUNCATION)
You MUST deliver the repo in STAGES. Do NOT omit code “for brevity”.
Stage A: Repo scaffold + config + layout + libs + SEO endpoints + devcontainer + tooling.
Stage B: Components/sections + pages/routes (Home, Emergency service pages, Pricing, Service Areas, Reviews, About, Contact, Policies, Privacy, Terms, 404).
Stage C: QA checklist + README + final notes (build/lint/dev).

If you reach output limits mid-stage, STOP and print: “STOPPED AT: <filepath>”.

QUALITY BAR (MUST PASS)
- npm run dev
- npm run build
- npm run lint
- No runtime errors.
- No lorem ipsum. Unknown inputs must be explicit: "TODO:INPUT".

CODE COMMENTARY (FOR AI ITERATION)
- Add concise comments:
  - 1–2 line header per file: purpose.
  - Short “why” comments for non-obvious logic.
  - TODOs must be explicit: TODO:INPUT or TODO:PROD (with next action).
- Do not add excessive commentary.

NON-NEGOTIABLE UX RULES
- Mobile-first.
- Sticky primary CTA = “Call Now” on every page (mobile + desktop) via layout.
- Mobile sticky bar:
  - Primary: Call Now (tel:)
  - Secondary: Text/SMS (optional, if configured)
- Add global bottom padding so sticky bar never covers content.
- Above the fold on Home and on every Emergency page:
  - Call CTA (one tap)
  - Service area line (e.g., “Serving Dallas-Fort Worth”)
  - Proof row (reviews, licensed/insured placeholders)
- Avoid distracting nav: keep top nav minimal (Home, Services, Service Areas, Reviews, Contact).

MODERN DESIGN ACCEPTANCE CRITERIA (STRICT)
- Single container system + consistent vertical rhythm (py-12/py-16).
- Hero headline 3xl–5xl; readable body.
- Buttons: primary + secondary with hover + focus-visible.
- Cards: consistent radius + subtle border/shadow.
- High contrast for emergency CTA (but do not hardcode colors beyond Tailwind defaults).

HOMEPAGE STRUCTURE (ORDER IS MANDATORY)
1) EmergencyHeroSection
   - Headline (e.g., “Emergency Plumbing — Call Now”)
   - Subheadline (response expectations as TODO:INPUT)
   - Primary Call Now CTA
   - Optional “Text Us” CTA if enabled
   - Proof row (reviews count placeholder, licensed/insured placeholder)
2) SymptomServicesSection
   - 6–9 “symptom-based” emergency links (e.g., “No heat”, “Burst pipe”)
3) PricingExpectationsSection
   - trip fee / range language (TODO:INPUT)
4) ServiceAreaSection
   - list of core cities/neighborhoods (config-driven)
5) TrustSection
   - testimonials + badges/credentials placeholders
6) FAQSection
   - 3–6 FAQs (availability, what to do while waiting, payment methods)
7) CTASection
   - Repeat Call Now CTA

CANONICAL FILE TREE (MUST MATCH EXACTLY)
- src/
  - app/
    - layout.tsx
    - globals.css
    - page.tsx                          (Home)
    - services/page.tsx                 (Services hub)
    - services/[slug]/page.tsx          (Emergency service detail, symptom-based)
    - pricing/page.tsx                  (Pricing expectations)
    - service-areas/page.tsx            (Areas hub)
    - service-areas/[city]/page.tsx     (City page)
    - reviews/page.tsx
    - about/page.tsx
    - contact/page.tsx
    - policies/page.tsx
    - privacy/page.tsx
    - terms/page.tsx
    - not-found.tsx
    - api/
      - lead/route.ts                   (minimal callback request, optional)
    - robots.ts
    - sitemap.ts
  - components/
    - Header.tsx
    - Footer.tsx
    - StickyCTA.tsx
    - JsonLd.tsx
    - NAP.tsx
    - ContactMethods.tsx
    - CallbackForm.tsx                  (minimal; LAST RESORT)
    - ProofStack.tsx
    - Testimonials.tsx
    - FAQ.tsx
    - ServiceCards.tsx
    - sections/
      - EmergencyHeroSection.tsx
      - SymptomServicesSection.tsx
      - PricingExpectationsSection.tsx
      - ServiceAreaSection.tsx
      - TrustSection.tsx
      - FAQSection.tsx
      - CTASection.tsx
  - config/site.ts
  - lib/
    - tracking.ts
    - analytics.ts
    - schema.ts
    - seo.ts
    - rateLimit.ts
    - utils.ts
- .devcontainer/devcontainer.json
- README.md
- package.json
- tailwind.config.ts
- postcss.config.js
- tsconfig.json
- eslint config

CONFIG (SINGLE SOURCE OF TRUTH) — EXACT TYPES REQUIRED
In src/config/site.ts define and export these EXACT interfaces and config object. Do not rename fields.

type AnalyticsConfig =
  | { provider: "none" }
  | { provider: "ga4"; ga4MeasurementId: string }
  | { provider: "plausible"; plausibleDomain: string };

type SpamProtectionConfig = {
  turnstileEnabled: boolean;
  turnstileSiteKey?: string;
  turnstileSecretKey?: string;
};

type CallConfig = {
  phoneDisplay: string;           // what user sees
  phoneDial: string;              // tel: target
  smsDisplay?: string;            // optional
  smsDial?: string;               // sms: target or tel: fallback
  callTrackingEnabled: boolean;
  trackingNumberDisplay?: string; // optional display if using tracking
  trackingNumberDial?: string;    // optional tel target for tracking number
};

type PricingExpectations = {
  tripFeeText: string;            // TODO:INPUT
  rangeText: string;              // TODO:INPUT
  disclaimerText: string;         // e.g., “Final price depends on diagnosis.”
};

type EmergencyService = {
  slug: string;
  name: string;                   // e.g., “Burst Pipe”, “No Heat”
  shortDescription: string;
  symptoms: string[];             // bullet list of symptoms
  whatToDoNow: string[];          // safety steps (non-harmful, general)
  serviceAreaNotes?: string;
};

type ServiceAreaCity = {
  city: string;
  headline: string;
  paragraphs: [string, string, ...string[]]; // 2+ unique paragraphs to avoid thin pages
};

export interface SiteConfig {
  baseUrl: string; // TODO:INPUT
  businessName: string;
  tagline: string;

  call: CallConfig;

  address: { serviceAreaOnly: true } | { line1: string; line2?: string; city: string; state: string; zip: string };
  hours: { day: string; open: string; close: string; closed?: boolean }[]; // allow 24/7 patterns (TODO:INPUT)
  serviceAreaCities: string[];

  emergencyServices: EmergencyService[];
  serviceAreas: ServiceAreaCity[];

  pricing: PricingExpectations;

  proof: { yearsInBusiness?: string; credentials?: string[]; guarantees?: string[] }; // TODO:INPUT
  reviews: { highlightQuotes: { name?: string; text: string }[]; reviewPlatformLinks: { label: string; url: string }[] };
  faqs: { q: string; a: string }[];

  callbackCaptureEnabled: boolean;     // if true, show CallbackForm on /contact only
  leadRouting: { webhookUrl?: string };// TODO:INPUT

  seo: { siteTitle: string; titleTemplate: string; metaDescription: string; primaryServiceKeywords: string[]; ogImagePath?: string };
  analytics: AnalyticsConfig;
  spamProtection: SpamProtectionConfig;
}

export const siteConfig: SiteConfig = { ... } // populate with TODO:INPUT placeholders

CALL BEHAVIOR (DETERMINISTIC)
- All “Call Now” buttons must call a single helper:
  - getDialNumber() returns trackingNumberDial if callTrackingEnabled and set, else phoneDial
  - display number shows trackingNumberDisplay if enabled, else phoneDisplay
- All tel: clicks fire event phone_click with context (page, service slug if applicable).

CALLBACK FORM (OPTIONAL, LAST RESORT)
- Only enabled if callbackCaptureEnabled === true.
- Must include honeypot + rate limiting (best-effort) + optional Turnstile verification.
- /api/lead should accept callback requests and forward to webhookUrl if present.

ANALYTICS (STRICT)
- Standard events:
  phone_click, sms_click, cta_call_click, directions_click, lead_form_submit, lead_form_success, lead_form_error
- If GA4 selected: use @next/third-parties/google GoogleAnalytics in layout (do not hand-roll scripts). :contentReference[oaicite:6]{index=6}
- track() logs to console and forwards to provider if enabled.

SEO RULES (STRICT)
- Canonical URLs via Metadata API: alternates.canonical.
- robots.ts must include Sitemap: `${baseUrl}/sitemap.xml`.
- sitemap.ts must include:
  - /, /services, /pricing, /service-areas, /reviews, /about, /contact, /policies, /privacy, /terms
  - plus each /services/[slug] and /service-areas/[city]
- Service-area pages must have 2+ unique paragraphs from config (avoid thin/duplicate pages). :contentReference[oaicite:7]{index=7}

SCHEMA (JSON-LD)
- Home + Contact: LocalBusiness (or ServiceAreaBusiness using serviceAreaOnly)
- Service pages: Service schema where appropriate
- BreadcrumbList internal
- FAQPage where FAQs render

NOW EXECUTE STAGE A, then STAGE B, then STAGE C in the same response if possible.
