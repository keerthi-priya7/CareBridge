# CareBridge AI

CareBridge AI is a family care coordination prototype for the Scaler Young Innovators Internship Challenge. It centers family members and authorized caregivers as the people who manage updates, so an older adult does not need a smartphone or an account to receive care.

## Run locally

Requirements: Node.js 20.19+ or 22.12+ and npm.

```sh
npm install
npm run dev
```

To make a production build and preview it:

```sh
npm run build
npm run preview
```

## Demo

Choose **Explore with demo data** from Sign Up or Log In. The fictional Ananya, Lakshmi Amma, Ravi, and Sneha care space supports check-ins, task completion, and adding sample medicines and tasks. Changes are stored in this browser's local storage. Use Settings → Reset demo data to clear them.

Google and email authentication are UI placeholders; no identity provider is connected. The care recap is generated from the locally recorded demo state and is not a server-side AI service. Community helper cards are fictional examples and no requests are sent to real people. Do not enter real health information in this prototype.

## Configuration

There are no API credentials or external services required for the demo. A production Supabase integration should use a server-controlled environment and the public Supabase URL plus anon key (`VITE_SUPABASE_URL`, `VITE_SUPABASE_ANON_KEY`) only after enabling the schema and policies in `supabase/schema.sql`. Never put a Supabase service-role key or AI provider secret in a `VITE_` variable or browser code. Route AI requests through an authenticated server endpoint that only summarizes authorized, recorded care facts.

## Data and access

The `supabase/schema.sql` file provides a starting relational schema for users, care profiles, memberships, check-ins, medicines and logs, appointments, tasks, assistance requests, and notifications. It enables row-level security and scopes each policy to authenticated profile members. Review and adapt policies, consent handling, retention, and audit requirements before using real personal or health data.

## Deployment

Build with `npm run build` and deploy the generated `dist/` directory to any static host configured to serve `index.html` for client-side routes. Configure the host's fallback rewrite for `/app/*` paths. Authentication, database, and AI integrations are intentionally not presented as live until configured.

## Accessibility

The prototype includes responsive layouts, keyboard focus styles, labeled controls, reduced-motion support, and large-text and high-contrast toggles under Settings. English, Telugu, and Hindi are listed as language choices; translated UI copy is not yet wired up.
