# Group Activity Planner

A group activity planner: friends set their preferences, the app finds real local venues and events, AI shortlists the best fits, and everyone votes live.

> [!NOTE]
> Early development - currently in Sprint 0 (setup and planning).

## Why

Plans often fall through the cracks when a group tries to organise something together. The cinema doesn't sound quite right, the zoo has become boring, and there's no single place to see what's actually on locally - so the group chat goes quiet and nothing gets booked. This project aims to fix that.

## How it works

1. The organiser signs up and creates a group.
2. They send invite links to friends, family or colleagues.
3. The organiser starts a plan, choosing a date range and a voting deadline.
4. Invited members join and set their preferences:
   - Budget
   - Location
   - Activity type (e.g. live music, nightlife, theatre)
5. The app searches real local venues and events, then uses AI to shortlist the best matches for the whole group, with a short reason for each.
6. Everyone votes 👍 or 👎 on each shortlisted activity, and the results update live.
7. When everyone has voted or the deadline passes, the winning activity is shown to the group.

## What's interesting technically

- **AI ranking with guardrails** - Claude ranks real candidates and explains each pick. Its output is validated against the candidate list, so it can't invent venues.
- **Evaluated, not guessed** - a suite of fixed test scenarios runs in CI and blocks any prompt change that makes rankings worse.
- **Observability** - every AI call is traced in Langfuse with its cost, latency and prompt version.
- **Live voting** - vote counts update instantly across everyone's devices over WebSockets.
- **Real data** - venues from Google Places and events from Ticketmaster, fetched concurrently.

## Tech stack (planned)

| Area | Technology |
|---|---|
| Frontend | React, TypeScript, Vite, Tailwind CSS |
| Backend | Python, FastAPI, Pydantic |
| Database | PostgreSQL |
| AI | Claude API, Langfuse |
| Dev environment | Docker, Dev Containers |

## Project board

Our backlog, sprints and progress are public: [Group Activity Planner board](https://github.com/users/mrfield-dev/projects/1)

## Future ideas

- Suggest the cheapest way to book the winning activity
- Group transport planning
- Per-person availability (e.g. calendar integration)

## Team

- **Max Field** - [@mrfield-dev](https://github.com/mrfield-dev)
- **Oli Kay** - [@Pingu1311](https://github.com/Pingu1311)