# Web App Design — Brainstorming Checklist

When brainstorming a web application, every project has the same structural areas regardless of tech stack. Cover them in this order before writing any spec or implementation plan. Each area needs a decision, not just acknowledgment.

---

## 1. Users & Roles

- Who are the actors? List every distinct role.
- Are roles unified (same signup, different permissions) or separate (different flows, different onboarding)?
- What does each role do — what's their core action in the system?

> Every role gets its own flow in sections 3 and 4. Don't collapse roles prematurely.

---

## 2. Visual Style & Personality

- Who is the target audience? (Developers, executives, consumers, field workers?)
- What does the brand communicate? (Technical precision, trust, energy, simplicity?)
- Dark or light? Dense or spacious? Functional or expressive?

This sets the tone for every screen. Decide it once, apply it everywhere.

---

## 3. Auth & Entry Points

For each role:
- How do they arrive? (Direct URL, shared link, email invite, marketplace search?)
- How do they register? (Social login, email/password, SSO, invite-only?)
- Is there a pre-auth preview, or is everything gated?
- Are roles determined at signup, or can they switch?

---

## 4. User Flows — Screen by Screen

For each role, walk through every screen in chronological order:

- **Onboarding** — what steps does a new user complete before they reach their first value moment?
- **Core experience** — what does a typical session look like once they're set up?
- **Empty states** — what do they see before they have data?
- **Upgrade / conversion points** — where does a free user hit a limit and see a paid CTA?

Go one screen at a time. Don't design systems — design the sequence a user actually walks through.

---

## 5. Data Layer

Map the data before touching schema. Three questions:

**What raw inputs exist?**
Files (PDF, images, videos), form submissions, third-party API data, real-time streams. List every data source.

**What gets stored, and what shape does it take?**
For each data type, decide:
- Is it a file? Where does it live? (local volume, object storage)
- Is it structured? Does it need to be queried/searched, or just retrieved?
- Does the schema evolve quickly? (Prefer JSONB while iterating; promote to relational columns when search requirements are clear)

**What fields drive business logic?**
These must be structured columns, not buried in JSON:
- Fields used in filtering, search, or access control
- Fields shown in lists or cards (need to be fast to read)
- Fields that gate features (plan type, usage counters, status flags)

---

## 6. Out of Scope

List explicitly what is NOT being built in this phase. Out-of-scope items:
- Prevent scope creep during implementation
- Give future phases a starting list
- Signal to the agent what to ignore when asked about edge cases

---

## Checklist

- [ ] All roles identified
- [ ] Visual style decided
- [ ] Auth and entry point decided per role
- [ ] Every screen in every flow covered
- [ ] Data types mapped (files, structured, business-logic fields)
- [ ] Out of scope list written
