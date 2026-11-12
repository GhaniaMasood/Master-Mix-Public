<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="docs/logo-reversed.svg">
    <img src="docs/logo.svg" alt="Master Mix logo" height="96" />
  </picture>
</p>

<h1 align="center">Master Mix</h1>

<p align="center">
  <em>A mentor matching platform for SynBio Pakistan.</em><br/>
  Students swipe on mentors, mentors swipe back, and a mutual yes opens a conversation.
</p>

<p align="center">
  <strong>Status:</strong> pilot build, working end to end &nbsp;|&nbsp;
  <strong>Built by:</strong> Ghania Masood &nbsp;|&nbsp;
  <strong>Source code:</strong> private (walkthrough available on request)
</p>

---

## Why this exists

Synthetic biology is a young field in Pakistan, and most undergraduates have nobody to ask: which research area fits me, how do I get into a lab, what does a PhD in this field actually involve? The few researchers who could answer are hard to reach without an existing connection.

[SynBio Pakistan](https://www.linkedin.com/company/SynBiopakistan) is a student-founded community that teaches synthetic biology for free through live lecture sessions. Master Mix is its mentorship layer: a simple way for students to find a mentor who has been where they are going, and for mentors to give a small amount of time to the right student.

The name is a small lab pun. In the lab, a master mix is the pre-made reaction mix you pipette into every tube. Here, MM also stands for mentor and mentee matching.


## How it works

1. **A student signs up** and fills in a profile: university, degree program, semester, research interests, what they want from a mentor, their goals, and a photo.
2. **They pay a small annual fee** (Easypaisa or JazzCash) and upload a screenshot as proof. The fee helps cover hosting, so the SynBio Pakistan workshops themselves can stay free.
3. **An admin approves** the payment, which unlocks the swipe deck.
4. **The student swipes through approved mentors.** Mentors who have reached their mentee limit drop out of the deck automatically, so nobody swipes into a dead end.
5. **Mentors see only the students who swiped right on them** and choose whether to swipe back.
6. **A mutual right swipe creates a match** and opens an in-app chat. From there the pair arranges a call on whatever platform suits them.

Mentor profiles are reviewed and approved by an admin before they appear to students.

## Key features

- **Mutual-consent matching.** A match only exists when both sides say yes. A database trigger creates the match the instant the second swipe lands.
- **Real swipe gestures.** Drag-to-swipe cards on touch and mouse, with tap buttons as a fallback.
- **Capacity limits per mentor.** Mentors set how many mentees they can take, which stops a few popular mentors from being overwhelmed.
- **Three roles.** Student, mentor and admin, each with their own views and access rules.
- **Admin dashboard.** Review payment proofs, approve or reject mentor profiles, and see live counts of students, mentors and matches.
- **Realtime chat** between matched pairs, with a report button for basic moderation.
- **Profile photos** on every card, so the platform feels human rather than anonymous.

## Design decisions

- **Why swipe?** Mentorship works best when both people choose each other. Mutual selection also means a mentor never receives a cold request from someone they did not see first.
- **Why mentor limits?** Without them the platform becomes a popularity contest, with every student swiping on the same few well-known people.
- **Why manual payment checks?** For a pilot of a few dozen people, verifying a screenshot by hand costs nothing and avoids payment gateway fees and business registration. It is a deliberate choice for this stage, not a gap.
- **Privacy by default.** Every table has row-level security, so users can only read and write what they are meant to. Payment screenshots are stored privately, and chat messages are visible only to the two people in a match.
- **Brand.** A warm plum palette and a high-contrast serif (Playfair Display for the logo, Fraunces for headings, Inter for body text) to feel considered and credible to both students and senior researchers.

## Tech stack

| Layer | Technology |
| --- | --- |
| Frontend | React 18, Vite, React Router |
| Swipe interaction | react-tinder-card, react-spring |
| Backend | Supabase (PostgreSQL, Auth, Storage, Realtime) |
| Security | Postgres Row Level Security policies on every table |
| Matching logic | PL/pgSQL trigger that creates a match on mutual right swipes |
| Design | Playfair Display, Fraunces, Inter; custom logo built from vector letterforms |

## Data model

Six tables: `profiles`, `payments`, `swipes`, `matches`, `messages`, `reports`, plus two storage buckets (private payment proofs, public profile photos). Roles and approval states are enforced in the database, not just in the interface.

## Roadmap

- [ ] Public deployment and first cohort of about 10 mentors
- [ ] Email notifications for approvals and new matches
- [ ] Mentors editing their own capacity and availability
- [ ] In-app feedback form to collect ratings from early users
- [ ] Optional automated payment verification once the pilot proves demand

## About the builder

I am an undergraduate biotechnology student in Pakistan and the founder of SynBio Pakistan. I built Master Mix end to end: product design, database design, security rules, frontend, and brand identity.

**Ghania Masood** | [LinkedIn](https://www.linkedin.com/in/ghania-masood-391540365)

---

<sub>The source code is kept in a private repository. This page is a public overview of the project.</sub>

