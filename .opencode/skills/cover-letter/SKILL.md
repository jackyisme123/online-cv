---
name: cover-letter
description: Use when asked to write, generate, tailor, or refine a cover letter (sollicitatiebrief) based on CV data and a job description, adhering to Dutch and international hiring standards.
---

# Cover Letter Generator (Dutch & International Standard)

This skill guides you through crafting a compelling, role-specific cover letter tailored to a target position and company culture, grounded in the candidate's CV (e.g., `_data/data.yml`), while strictly avoiding duplication of CV content.

---

## 1. Golden Rules for Dutch & International Cover Letters

Dutch recruiters and hiring managers value authenticity, modesty, and directness ("doe maar gewoon"). Follow these core constraints:

1. **Length**: Maximum one single A4 page (~250 to 400 words, 3 to 5 focused paragraphs).
2. **Tone**: Professional, straightforward, active, and grounded.
   - **Show, Don't Tell**: Never use empty buzzwords like "results-driven team player", "passionate guru", or "hard-working problem solver". Replace them with concrete situations, actions, and quantifiable outcomes.
3. **Short, Clear Sentences (High Readability)**:
   - Avoid long, convoluted, multi-clause sentences. Long sentences are hard to read and often sound robotic.
   - Split complex sentences into simple, direct ones.
   - Aim for crisp statements that recruiters can scan effortlessly.
4. **No Em-Dashes (`—`) or Parenthetical Acronyms (e.g., `(SCM)`)**:
   - Never use em-dashes (`—`) or en-dashes (`–`) for mid-sentence pauses or breaks. Use standard periods, commas, or natural transitions instead. Em-dashes often look artificial or AI-generated.
   - Never introduce acronym definitions in parentheses like `"Source Control Management (SCM)"`, `"Continuous Integration (CI)"`, or `"Site Reliability Engineering (SRE)"`. Write the term naturally or use standard industry terms directly without parenthetical explanations. A cover letter is human correspondence, not a technical manual.
5. **No Generic Copies / Templates**: Every letter must be written from scratch for the specific role and company. Generic or templated letters are easily spotted and dismissed.
6. **Complement, Do Not Duplicate CV**:
   - The CV states *what* was done and *where*.
   - The cover letter explains *why* the candidate is pursuing this specific role, *how* their mindset and approach solve the company's problems, and *what drives* them.

---

## 2. Mandatory Core Traits to Weave In

Every generated cover letter **must** naturally weave in three fundamental traits with factual backing (never as bare assertions):

| Trait | What it Demonstrates | Example Factual Backing |
| :--- | :--- | :--- |
| **1. Good fit for an international environment** | Cross-cultural communication, working across global teams/timezones, remote/hybrid collaboration, fluency in international business English. | Experience collaborating with global enterprise clients (e.g., across AU, NZ, Europe, APAC), cross-functional squads, diverse stakeholder management. |
| **2. Keen and eager to learn new tech or skills** | Intellectual curiosity, proactive self-directed learning, staying ahead of industry shifts (e.g., AI/ML, cloud, DevOps). | Continuously obtaining certifications (AWS, GitHub Actions, AI), adopting cutting-edge tools (FastMCP, agentic frameworks, OpenTelemetry), and mentoring others. |
| **3. Ownership of tasks** | End-to-end accountability, initiative to resolve root causes rather than just surface symptoms, driving operational and cultural improvements. | Leading transitions (e.g., Ops-to-SRE), authoring runbook-as-code auto-remediations, stepping up as incident commander/bridge lead, eliminating toil proactively. |

---

## 3. Workflow (Always Follow in Sequence)

### Phase 1: Intake & Discovery (NEVER Skip)
Before generating any letter, inspect `_data/data.yml` to understand the candidate's background. If the user has not provided the necessary job details, **promptly ask for**:

1. **Job Description (JD)**: The full text or key requirements of the vacancy.
2. **Company & Recruiter Details**:
   - Company name and website/context.
   - Specific name of the hiring manager or recruiter (or search hint, e.g., from LinkedIn/job post).
   - Platform/source where the vacancy was found (e.g., LinkedIn, company careers page).
3. **Language Preference**:
   - English (standard for most international/tech companies in the Netherlands).
   - Dutch (for domestic companies or Dutch-language postings).
4. **Work Authorization & Expat Practicalities**:
   - Confirm current location (e.g., New Zealand looking to relocate to Amsterdam, Netherlands).
   - Target start date or visa/sponsorship requirements (e.g., Highly Skilled Migrant / Kennismigrant sponsorship needed or EU citizenship status).

### Phase 2: Research, Analysis & Matchmaking
1. **Search & Research Company Culture**:
   - Actively search the company's website, about/careers page, and engineering blog.
   - Look up company culture, core values, working philosophy, tech stack, and recent initiatives or public news.
   - Identify the tone of the organization (casual/tech/startup vs. structured/enterprise).
   - Use these concrete findings to tailor the letter's motivation section with specific, genuine references rather than generic compliments.
2. **Analyze the JD Requirements**:
   - Extract the top 2–3 core technical and cultural requirements.
   - Identify the primary challenges or operational friction the team aims to solve.
3. **Map Experience without Duplicating**:
   - Select 2–3 distinct stories from the candidate's CV (`_data/data.yml`) that directly answer the JD's key requirements.
   - Frame each story through the lens of: **Challenge Faced -> Proactive Action & Ownership -> Business / Technical Impact**.
   - Keep each story concise, using short, simple sentences rather than lengthy multi-clause explanations.
   - If a key skill mentioned in the JD is ambiguous in the CV, ask the user: *"The JD heavily emphasizes [Topic X]. Do you have a specific project or achievement we should highlight for this?"*

### Phase 3: Drafting (Structured Layout)
Construct the letter adhering strictly to the 5-part structure below. Keep sentence structures simple and direct throughout all sections. Split long thoughts into multiple short sentences.

---

## 4. Recommended Structure

### 1. Header & Salutation
- **Candidate Contact Information**: Name, Location (with relocation note), Email, Phone, LinkedIn/GitHub links.
- **Date**: e.g., `15 November 2026` or `15 november 2026`.
- **Company Information**: Company Name, Department, City, Country.
- **Subject Line**: e.g., `Application: [Job Title] (Ref / Vacancy Source)` or `Betreft: Sollicitatie [Functietitel]`.
- **Salutation**:
  - *Informal / Tech / Startup culture*: `Dear [First Name],` (EN) / `Beste [Voornaam],` (NL).
  - *Formal / Enterprise culture*: `Dear Mr./Ms. [Last Name],` (EN) / `Geachte heer/mevrouw [Achternaam],` (NL).
  - *Fallback if name unknown*: `Dear [Company Name / Engineering] Hiring Team,` (EN) / `Geachte selectiecommissie,` (NL).

### 2. Opening Paragraph: The Hook
- Catch attention immediately with an authentic, non-cliché opening.
- Clearly state the target position, where it was spotted, and why this specific team/mission resonated immediately.
- *Avoid*: "I am writing to express my enthusiastic interest in..." or "I am the ideal candidate for..."
- *Prefer*: Directly connecting the company's current engineering or business challenge to your professional focus.

### 3. Body Paragraphs: Suitability, Match & Practicalities (1–2 paragraphs)
- Connect 2–3 key job requirements to real accomplishments.
- Detail the *approach* and *impact* (e.g., latency reduction, toil elimination, cross-functional incident leadership).
- Subtly highlight **ownership** and **learning agility**.
- **Expat & Practicalities Note**: In 1–2 concise sentences, state the relocation readiness, visa situation (e.g., requiring Highly Skilled Migrant sponsorship), and English/Dutch language capabilities.

### 4. Motivation: Why Them? (1 paragraph)
- Answer: *"Why this company, and why now?"*
- Reference their architecture, product values, scale, international team dynamics, or engineering culture.
- Reiterate how thriving in an **international environment** aligns with your career trajectory.

### 5. Closing & Call to Action
- Maintain a direct, confident, and professional tone.
- Express enthusiasm for an introductory conversation / interview.
- *Dutch phrasing*: `"Ik zie uit naar een kennismakingsgesprek om mijn motivatie en achtergrond nader toe te lichten."`
- *English phrasing*: `"I welcome the opportunity to discuss how my background and hands-on approach align with [Company]'s engineering goals in an introductory interview."`
- **Sign-off**:
  - English: `Kind regards,` or `Sincerely,`
  - Dutch: `Met vriendelijke groet,`
  - Candidate Full Name.

---

## 5. Tone & Style Checklist

Before presenting the letter to the user, verify against these criteria:

- [ ] **One Page / Under 400 words**: Can it be read comfortably in under 90 seconds?
- [ ] **Short, Simple Sentences**: Are long, complex sentences split into simple, digestible ones for effortless reading?
- [ ] **No Em-Dashes (`—`)**: Are all em-dashes and en-dashes removed in favor of standard periods or commas?
- [ ] **No Parenthetical Acronyms**: Are terms written naturally without textbook-style parenthetical definitions like `(SCM)` or `(CI/CD)`?
- [ ] **Company Culture Grounded**: Has the company culture, mission, or engineering blog been researched and reflected with specific details?
- [ ] **No Copy-Paste of CV**: Does it avoid simply regurgitating resume bullet points?
- [ ] **All 3 Traits Present with Proof**:
  - [ ] International environment fit (collaborative, cross-cultural, communication)
  - [ ] Eagerness to learn new technology (certifications, AI tools, self-driven upskilling)
  - [ ] Ownership of tasks (end-to-end accountability, initiative, toil reduction)
- [ ] **No Clichés**: Filter out words like "synergy", "rockstar", "dynamic team player", "go-getter".
- [ ] **Specific & Factual**: Every claim is supported by a metric, project, or concrete technical outcome.
- [ ] **Relocation/Work Status Addressed**: Clear and transparent for Dutch/European recruiters.
