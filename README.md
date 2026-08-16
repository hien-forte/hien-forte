# Hi, I'm Hien 👋

### Technical Account Manager · Solutions Engineer · AI-Native Builder

I've spent about 10 years in fintech, payments, and SaaS as the technical person on enterprise accounts, first as a solutions engineer and later running technical account management. Over that stretch I launched 20+ API integration partnerships and wrote the specs behind them, kept a 98% retention rate on the accounts I owned, and had a hand in several million dollars of new business. I'm the person who's comfortable sitting in an executive review in the morning and heads-down on a broken integration by the afternoon.

Late in 2024 I stepped back from full-time work to be around for my son. I didn't sit still. I taught myself to ship real software by directing AI coding tools, and I used that to build and launch an actual product. He starts preschool this fall, so I'm ready to head back to full-time work with a lot more technical range than I had when I left.

## FORTE Health, the thing I built

[fortehealth.co](https://fortehealth.co) is a telehealth company I started and took all the way to a live, LegitScript-certified product, mostly on my own. I owned all of it: the brand, the marketing site, the patient intake, the portal with its provider and admin tools, Stripe billing, the compliance program, and the analytics and ad-tracking setup my marketing partner runs on now.

I'll be straight about how I built it, since it comes up in technical interviews. I didn't hand-write the production code. I wrote detailed specs, pointed Claude Code at them, and read every line that shipped. The architecture, the roadmap, and the build-or-buy calls were mine. It's honestly the same job I did as a solutions engineer, just closer to the keyboard: get up to speed on a new domain quickly and make a pile of separate systems behave like one product, this time with real healthcare compliance rules to stay inside of.

Today it's a working funnel end to end, from the marketing site through the questionnaire, clinician review, prescription, payment, and shipment tracking. I didn't treat compliance as an afterthought either. I built the HIPAA program (risk assessment, BAAs, policies) in from the start, and I ran a security audit of the backend before turning on any paid traffic.

## How it fits together

```mermaid
flowchart LR
    V([Visitor]) --> MKT[Marketing site<br/>Framer]
    MKT --> RT{Edge router<br/>Cloudflare Worker}
    RT --> INTAKE[Patient intake apps<br/>Cloudflare Pages]
    RT --> TH[Telehealth platform<br/>clinician review + Rx]
    INTAKE --> TH
    TH --> PAY[Payments<br/>Stripe]
    TH --> PORTAL[Patient + provider + admin portal<br/>Supabase + edge functions]
    MKT & INTAKE & TH --> TRK[Analytics + ad attribution<br/>GTM · GA4 · Meta CAPI]
    PORTAL --> DB[(Postgres + RLS)]
```

*This is the high-level shape. The code itself is private since it's a live healthcare app, but I'm glad to walk through it.*

Under the hood: Cloudflare (Workers, Pages, DNS, edge rules), Supabase and Postgres with row-level security and edge functions, Stripe, a telehealth engine, Framer, and a GTM / GA4 / Meta Conversions API tracking pipeline.

## Kopperss Design, the studio side

The client work grew into a proper studio: [Kopperss Design](https://kopperssdesign.com). Same method as FORTE, applied to other people's brands. Every project starts with the same questions: who is this brand, what do they want to portray, and how do they want to interact with their customers? Once I have those answers I design and build the whole thing, front end to back end. I built the studio's own identity too, from the logo system to the landing page, and the site doubles as the portfolio with live, clickable versions of each build.

Four client builds so far:

- **[JadeCow Creamery](https://jadecowcreamery.com)** hired me to build their website and a custom CRM. The CRM pulls in their point-of-sale data, cleans it up, ties it to their customer list and email signups, and tracks promo codes, campaigns, and what each customer spends. I then shipped a fully functioning outbound email marketing inside their admin portal: campaigns to the full list or selected members, five branded templates plus a custom template builder, and live DKIM-authenticated sending from their own domain on Cloudflare's email infrastructure. Different world from telehealth, real client, real deadline, and the approach held up.
- **[Delicious Donuts](https://kopperssdesign.com/deliciousdonuts/)** is a Portland institution whose site hadn't been touched since 2016. I audited the old site, rebuilt their brand kit from the logo up, and designed a five-page redesign with imagery I generated to match. Then I built them a [custom online ordering page](https://kopperssdesign.com/deliciousdonuts/order/) that integrates directly with their Clover POS: card checkout with payment processing, promo codes, tips, and their real baker's dozen pricing worked into the cart logic. The [before and after](https://kopperssdesign.com/compare/deliciousdonuts/) says it better than I can.
- **[Sap Heng Thai & Laos](https://kopperssdesign.com/sapheng/)** is a locally operated, family owned Thai and Lao food cart in Portland with nothing online but a Facebook page, an Instagram, and a handful of Yelp reviews. I rebuilt their brand from the ground up: a full brand kit, a logo suite in three lockups, a hand-illustrated website carrying their complete 60-item menu, ad creatives, and a new print-ready menu board, all matched to their existing online presence and shaped by direction from the owners to bring forth one cohesive brand identity.
- **[Dee's Auto Garage](https://kopperssdesign.com/deesauto/)** *(in progress)* is an independent two-bay shop in Portland that was running its whole business out of Instagram DMs. They had a logo and nothing else. I built the [full brand system](https://kopperssdesign.com/deesauto/brand) out from that badge, then a site that replaces "DM me for a quote" with a real intake form capturing vehicle, mileage, modifications and symptoms. Every photo on it is the shop's own work, pulled from their feed and put through one grading pass so forty-five phone snaps read as a single set. Phase two is a [complete shop operating system](https://kopperssdesign.com/deesauto/crm/), wireframed end to end: a job board from request to collection, digital vehicle inspections, estimates a customer approves line by line from their phone with the total updating live, and reports with revenue forecasting capped by real bay capacity.

The thread through all of it: design and engineering are one process for me, not a handoff. The same project that gets the brand kit and the art direction also gets the CRM, the payment processing, or the POS integration, and it ships as one product. Telehealth compliance, ice cream loyalty data, donut shop point of sale, food cart branding, auto shop operations. The domain changes, the end-to-end approach doesn't.

## How I work

Hand me a messy problem and not much runway and I'm happy. I get to know the domain, figure out the one or two things that actually move the needle, build the smallest version that works, and then make it solid. I care about shipping, and I care about whoever ends up using the thing. That second part comes straight from ten years of pre-sales and account management.

Day to day I lean on Claude Code and Cursor to build, ChatGPT and Perplexity to research and think through problems, Gumloop for automation, and Higgsfield and Claude for design, plus Figma, Framer, and Supabase.

## Before this

- **Toast**, Senior Solutions Engineer. Ran the technical sale and delivery for a national brand's move off legacy Micros, a 16-month phased rollout with no disruption, and built out 20+ third-party API integrations, writing the specs and running the developer enablement behind them.
- **Otter**, Technical Account Manager. Took a near-churn enterprise client with 1,700+ storefronts from a 75% integration success rate to 98% in two quarters. The real fix was a missing change-management process, so I built the SOP and monitoring and we landed a three-year renewal.
- **Docusign**, Technical Customer Success Manager. Owned post-sale for enterprise financial-services accounts and caught integration problems with API and SQL analysis before customers ran into them.

Full history is on LinkedIn.

## Find me

- 🌐 My product: [fortehealth.co](https://fortehealth.co)
- 🎨 My studio: [kopperssdesign.com](https://kopperssdesign.com)
- 🍦 Client builds: [jadecowcreamery.com](https://jadecowcreamery.com) · [Delicious Donuts](https://kopperssdesign.com/deliciousdonuts/) · [Sap Heng Thai & Laos](https://kopperssdesign.com/sapheng/) · [Dee's Auto Garage](https://kopperssdesign.com/deesauto/)
- 💼 LinkedIn: [in/hnguyen05](https://www.linkedin.com/in/hnguyen05/)
- 📫 hien.nguyen.work86@gmail.com

I'm looking for Forward-Deployed Engineer, Solutions Engineering, and technical account management roles, remote in the US.
