# TODO.md — Emergency / Dispatch Template

## Stage A: Repo Scaffold + Config + Layout + Libs + SEO + Tooling

- [ ] Initialize Next.js project with App Router, TypeScript, Tailwind CSS
- [ ] Create `package.json` with required dependencies
- [ ] Create `tailwind.config.ts`
- [ ] Create `postcss.config.js`
- [ ] Create `tsconfig.json`
- [ ] Create ESLint config
- [ ] Create `.devcontainer/devcontainer.json`
- [ ] Create `src/config/site.ts` with exact interfaces and config object (populate with `TODO:INPUT` placeholders)
- [ ] Create `src/app/layout.tsx` (includes Sticky CTA, global styles, analytics)
- [ ] Create `src/app/globals.css`
- [ ] Create `src/lib/tracking.ts` (phone_click, sms_click, cta_call_click, etc.)
- [ ] Create `src/lib/analytics.ts` (GA4/Plausible/none support)
- [ ] Create `src/lib/schema.ts` (JSON-LD helpers)
- [ ] Create `src/lib/seo.ts` (metadata helpers)
- [ ] Create `src/lib/rateLimit.ts`
- [ ] Create `src/lib/utils.ts` (getDialNumber, getDisplayNumber helpers)
- [ ] Create `src/app/robots.ts`
- [ ] Create `src/app/sitemap.ts`

---

## Stage B: Components/Sections + Pages/Routes

### Components

- [ ] `src/components/Header.tsx` — Minimal nav (Home, Services, Service Areas, Reviews, Contact)
- [ ] `src/components/Footer.tsx`
- [ ] `src/components/StickyCTA.tsx` — Mobile sticky bar (Call Now primary, optional SMS secondary)
- [ ] `src/components/JsonLd.tsx`
- [ ] `src/components/NAP.tsx` — Name, Address, Phone
- [ ] `src/components/ContactMethods.tsx`
- [ ] `src/components/CallbackForm.tsx` — Minimal, last resort; honeypot + rate limiting + optional Turnstile
- [ ] `src/components/ProofStack.tsx` — Reviews, licensed/insured badges
- [ ] `src/components/Testimonials.tsx`
- [ ] `src/components/FAQ.tsx`
- [ ] `src/components/ServiceCards.tsx`

### Sections (for Homepage)

- [ ] `src/components/sections/EmergencyHeroSection.tsx`
- [ ] `src/components/sections/SymptomServicesSection.tsx`
- [ ] `src/components/sections/PricingExpectationsSection.tsx`
- [ ] `src/components/sections/ServiceAreaSection.tsx`
- [ ] `src/components/sections/TrustSection.tsx`
- [ ] `src/components/sections/FAQSection.tsx`
- [ ] `src/components/sections/CTASection.tsx`

### Pages/Routes

- [ ] `src/app/page.tsx` — Home (EmergencyHeroSection, SymptomServicesSection, PricingExpectationsSection, ServiceAreaSection, TrustSection, FAQSection, CTASection)
- [ ] `src/app/services/page.tsx` — Services hub
- [ ] `src/app/services/[slug]/page.tsx` — Emergency service detail (symptom-based)
- [ ] `src/app/pricing/page.tsx` — Pricing expectations
- [ ] `src/app/service-areas/page.tsx` — Areas hub
- [ ] `src/app/service-areas/[city]/page.tsx` — City page (2+ unique paragraphs)
- [ ] `src/app/reviews/page.tsx`
- [ ] `src/app/about/page.tsx`
- [ ] `src/app/contact/page.tsx`
- [ ] `src/app/policies/page.tsx`
- [ ] `src/app/privacy/page.tsx`
- [ ] `src/app/terms/page.tsx`
- [ ] `src/app/not-found.tsx`
- [ ] `src/app/api/lead/route.ts` — Minimal callback request endpoint (optional)

---

## Stage C: QA Checklist + README + Final Notes

### QA Checklist

- [ ] `npm run dev` — No runtime errors
- [ ] `npm run build` — Successful build
- [ ] `npm run lint` — No lint errors
- [ ] No lorem ipsum in code; all unknown inputs marked as `TODO:INPUT`
- [ ] Mobile-first responsive design verified
- [ ] Sticky CTA visible and functional on mobile + desktop
- [ ] Call Now is dominant CTA on every page
- [ ] Above-the-fold trust signals present (license/insured, reviews, service area)
- [ ] Pricing Expectations section includes trip fee / range language
- [ ] Call tracking hooks functional (config-driven)
- [ ] JSON-LD schemas present (LocalBusiness, Service, FAQPage, BreadcrumbList)
- [ ] Canonical URLs set via Metadata API
- [ ] robots.ts includes Sitemap reference
- [ ] sitemap.ts includes all static and dynamic routes
- [ ] Service-area pages have 2+ unique paragraphs (no thin/duplicate content)
- [ ] Analytics events firing correctly (phone_click, sms_click, cta_call_click, etc.)
- [ ] CallbackForm (if enabled) has honeypot, rate limiting, optional Turnstile

### README

- [ ] Create `README.md` with:
  - Project overview
  - Stack details (Next.js, TypeScript, Tailwind CSS)
  - Setup instructions (install, dev, build, lint)
  - Configuration guide (`src/config/site.ts`)
  - Deployment notes

---

## TODO:INPUT Placeholders to Fill

- [ ] `baseUrl` — Production URL
- [ ] `businessName` — Business name
- [ ] `tagline` — Business tagline
- [ ] `phoneDisplay` / `phoneDial` — Primary phone number
- [ ] `smsDisplay` / `smsDial` — Optional SMS number
- [ ] `trackingNumberDisplay` / `trackingNumberDial` — Call tracking number (if enabled)
- [ ] `address` — Business address or `serviceAreaOnly: true`
- [ ] `hours` — Business hours (support 24/7 patterns)
- [ ] `serviceAreaCities` — List of cities/neighborhoods served
- [ ] `emergencyServices` — Emergency services with slugs, names, symptoms, safety steps
- [ ] `serviceAreas` — City pages with 2+ unique paragraphs each
- [ ] `pricing.tripFeeText` — Trip/diagnostic fee language
- [ ] `pricing.rangeText` — Typical price range language
- [ ] `proof.yearsInBusiness` — Years in business
- [ ] `proof.credentials` — Licenses, certifications, badges
- [ ] `proof.guarantees` — Guarantees offered
- [ ] `reviews.highlightQuotes` — Customer testimonial quotes
- [ ] `reviews.reviewPlatformLinks` — Links to Google, Yelp, etc.
- [ ] `faqs` — 3–6 FAQs (availability, what to do while waiting, payment methods)
- [ ] `leadRouting.webhookUrl` — Webhook URL for callback form submissions
- [ ] `seo.*` — Site title, meta description, keywords, OG image
- [ ] `analytics.ga4MeasurementId` or `analytics.plausibleDomain` — Analytics config
- [ ] `spamProtection.turnstileSiteKey` / `turnstileSecretKey` — Turnstile keys (if enabled)
