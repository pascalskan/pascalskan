**Looking for a junior or graduate role in data, machine learning or software engineering. UK-based or remote, available now.**

Computer Science graduate (Newcastle, 2026). Based in Leicester, willing to
relocate. Currently building and maintaining websites for two freelance clients.

Most of what I build is either a site somebody is relying on today, or a question I wanted a proper answer to.

Two of the five repositories here are client work and are private, so what you can read is a subset. Short descriptions of both are below.

---

## Live client work

**Travel without Borders** — [travelwithoutborders.co.uk](https://travelwithoutborders.co.uk) · *private repo*

WordPress redevelopment for a UK travel company specialising in Germany. Live since August 2026, and still under active maintenance.

The theme and page builder are commercial and can't be modified, so every customisation lives in a child theme: 14 components, each with its own stylesheet loaded only where it is used. The work included bringing 59 destination pages onto one layout, a testimonials system built as custom page-builder elements, a trade page in English and German with its own enquiry form, and a consent gate that keeps analytics dormant until a visitor accepts.

One problem worth describing. The client asked how many people click a partner link. Three attempts through Google Analytics failed, and inspecting the published tag container explained why permanently: it contained no GA4 tag at all, only four dead Universal Analytics tags whose relay into GA4 suppresses the outbound-click measurement. Removing them needed access nobody could get. I built the counter into the site instead: a redirect endpoint that records the click and forwards the visitor. It stores no cookie, no IP and no identifier, which is why it needs no consent and therefore counts the visitors who decline it. Every figure in the analytics property was a floor; this one isn't.

**MG Drive Pro** — [mgdrivepro.co.uk](https://mgdrivepro.co.uk) · *private repo*

Marketing site for a driving instructor. Hand-written static HTML with no build step or framework, deployed on Netlify, with a FastAPI backend deployed separately.

Four pages demonstrating planned functionality are kept in the repository but disabled behind three independent layers: feature flags, a client-side guard that fails closed, and host-level redirects. One of them failing doesn't expose an unfinished feature.

---

## Public projects

### [temporal-strength-performance-prediction](https://github.com/pascalskan/temporal-strength-performance-prediction) · Python

Does machine learning actually predict competitive strength performance better than the formulas coaches already use, or does it just look that way?

Traditional methods (Epley, Brzycki) score extremely well under normal retrospective evaluation. The project's finding is that most of that score is reconstruction rather than prediction. Given the right evaluation split, the models are rebuilding outcomes they can already see. Under temporally consistent forward evaluation, using only information available before the competition being predicted, the rankings change.

Built on OpenPowerlifting competition data with engineered longitudinal features, a modular `src/`, deterministic validation fixtures and CI. The more useful result is the methodological one: how you evaluate changes which model wins.

### [Mind-Canvas](https://github.com/pascalskan/Mind-Canvas) · TypeScript

An infinite canvas of nested bubbles for whatever is taking up space in your head. A pnpm monorepo: React 19 on the web, Expo on mobile, an Express API, Postgres via Drizzle.

The interesting problems were in sync, not rendering. Automatic saving was built and then removed, because every edit hitting the network let a half-finished canvas on one device overwrite finished work on the other. A newer save is now offered and never applied silently. The two clients deliberately share no code, so a contract test imports all three implementations of the layout maths and validation (web, mobile, server) and asserts they agree. Divergence there would be silent, and silent is the failure mode worth testing for.

### [The-Ledger](https://github.com/pascalskan/The-Ledger) · TypeScript

An operational intelligence platform built around one rule: nothing becomes financially real until a person approves it. Timesheets, expenses and materials create submissions, not financial records. Automation can notify, escalate and schedule; it can never approve.

A high-fidelity frontend prototype on mock data, with the backend deliberately deferred. The approval and audit model is the hard part of the product, and it's cheaper to get it right in a working interface than to discover it's wrong after building a schema around it. React, TypeScript, Zustand, TanStack Query, Playwright end-to-end tests.

---

## How I work

I keep a written record of what changed and why, including the things that went wrong. The Travel without Borders repository has a document listing every error made since the site went live: defects that reached visitors, claims I made that turned out to be wrong, and the measurements that produced confident but false answers. That last category is the useful one. A check that quietly lies is more expensive than a bug, because you stop looking.

Two examples from that list. An image-weight fix cut page weight by 13% and I nearly reported it as a win. Measured properly it had increased the number of requests from 30 to 37, because the lazy-loader wrote `src` before `srcset` and the browser fetched both. And a sharpness check that scored 13 images as too low-resolution was using a property that is meaningless with responsive image sets; every one of those images was fine.

I verify against the thing itself rather than the tool that reports on it, and I'd rather say a result is unconfirmed than round it up.

---

**pskannavis@gmail.com** · [LinkedIn](https://www.linkedin.com/in/pascal-skannavis/)

*Leicester, willing to relocate. Available now.*
