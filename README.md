# Debt Escape OS

Debt Escape OS is a financial wellness dashboard concept designed to help people increase their debt velocity, find cash-flow leaks, and move their debt-free date closer.

## MVP preview

The current build is a responsive, seeded dashboard prototype featuring:

- Debt Velocity Index score and momentum metrics
- Debt-free date forecast
- Debt account progress and balances
- Money leak scanner quick wins
- Selectable 14, 30, and 90 day debt sprints
- Interactive AI Debt Coach modal

## Run locally

```bash
npm install
npm run dev
npm test
```

The app is intentionally seeded with sample data. Bank connections, authentication, billing, and production financial calculations are next-stage integrations.

The payoff calculation service now lives in [src/lib/payoff.ts](src/lib/payoff.ts) with focused tests. The secure API and PostgreSQL boundary is documented in [docs/BACKEND_FOUNDATION.md](docs/BACKEND_FOUNDATION.md); no production backend or real financial-data collection is connected yet.

## Supabase preparation

The repository includes a guarded client boundary in [src/lib/supabase.ts](src/lib/supabase.ts), a starter RLS migration in [supabase/migrations/202608260001_initial_schema.sql](supabase/migrations/202608260001_initial_schema.sql), and [.env.example](.env.example). The app remains local-only until a Supabase project is deliberately configured. Use only the publishable anonymous key in the browser; never expose a service-role key.

Authentication preparation is in [src/lib/auth.ts](src/lib/auth.ts) using passwordless email links. It is intentionally not connected to the dashboard yet. Before inviting real testers, use separate test accounts, obtain written informed consent, collect only the minimum needed data, and provide deletion/support instructions. Never use anyone else's credentials or bank login information.

The typed persistence boundary is in [src/lib/database.ts](src/lib/database.ts). It remains fail-closed until a configured and authenticated Supabase session exists. The next credential-dependent step is to create the Supabase project, apply the migration, and configure the redirect URL for magic links.

Follow [docs/SUPABASE_SETUP.md](docs/SUPABASE_SETUP.md) for the exact dashboard and `.env.local` steps. Never send credentials through chat.

## Monetization direction

Debt Escape OS should avoid nickel-and-dime feature gating. The preferred model is a transparent, all-access subscription with one meaningful plan, a generous trial or useful free preview, and no surprise limits on core debt-payoff workflows. Pricing should be tested with users before implementation; mobile subscriptions must also follow Apple and Google billing rules.

## Privacy and security

The prototype does not collect or transmit financial data. See [docs/PRIVACY_SECURITY_READINESS.md](docs/PRIVACY_SECURITY_READINESS.md) for the pre-launch engineering and legal review checklist. That document is guidance, not legal advice; qualified counsel must review the production data flows, claims, terms, and applicable jurisdictions before launch.
