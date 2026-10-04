# SafeEyes NG: Docs

> The front door of the SafeEyes NG project. Start here.

**SafeEyes NG** (working title) is an open-source, verified crowd-sighting and alert network for kidnapping cases in Nigeria. Communities act as **eyes, not fists**: people report what they see, trained verifiers confirm cases, and authorised responders act on consolidated evidence. Evidence integrity and incentives are built on the [Stellar](https://stellar.org) network.

This repository holds everything that is *not* code: the proposal, threat model, architecture, roadmap, governance, community playbooks and translations.

---

## Project at a glance

| | |
|---|---|
| **Mission** | Help communities share verified information fast enough to matter in the first hours of a kidnapping, without enabling mob violence or abuse |
| **Status** | Phase 0: Discovery (update this as the project moves) |
| **License** | Docs: CC BY 4.0. Code repositories: Apache-2.0 (confirm before first release) |
| **Chat / Discussions** | _Add link_ |
| **Maintainers** | _Add names and GitHub handles_ |

## The four repositories

| Repo | Purpose |
|---|---|
| [`docs`](.) | This repo: proposal, threat model, architecture, roadmap, governance |
| `backend` | API, case verification flow, sightings, geofencing, messaging gateway, evidence anchoring service |
| `frontend` | Offline-first mobile app and responder web dashboard |
| `contracts` | Soroban smart contracts: evidence anchor, reporter stake, reputation, escrow |

## How the system works (short version)

1. A family member, community leader or partner NGO opens a **case**.
2. Vetted **verifiers** confirm it, ideally within minutes.
3. A **geofenced alert** goes out by push, SMS, USSD and chat bots. It carries minimal detail and expires automatically.
4. Residents submit **sightings**: photo, video, voice note, text, or a consented live location.
5. Each upload is hashed on the device. The **hash and timestamp are anchored on Stellar**, while the files stay encrypted off-chain.
6. Verified responders see a **live case map and timeline**. The public is never told to go somewhere and confront anyone.

## Repository layout

```
docs/
├── README.md
├── proposal.md              # grant proposal
├── threat-model.md          # what can go wrong and how we handle it
├── architecture.md          # system design and data flow
├── roadmap.md               # phases 0 to 3, grant milestones
├── governance.md            # who decides what, how to become a maintainer
├── CONTRIBUTING.md          # how to contribute across all repos
├── CODE_OF_CONDUCT.md
├── SECURITY.md              # private vulnerability reporting
├── api/
│   └── openapi.yaml         # API contract shared by backend and frontend
├── adr/                     # architecture decision records (one file per decision)
├── community/
│   ├── verifier-guide.md    # how verifiers are recruited, trained and audited
│   ├── pilot-playbook.md    # running a community pilot
│   └── outreach/            # materials for NGOs, families, community groups
└── translations/
    ├── ha/                  # Hausa
    ├── yo/                  # Yoruba
    ├── ig/                  # Igbo
    └── pcm/                 # Nigerian Pidgin
```

## Design principles

These apply to every decision in every repo:

1. **Eyes, not fists.** The crowd gathers and relays information. Interventions are led by people trained and authorised to do them.
2. **Verify before broadcasting.** No public alert without human verification.
3. **Minimum necessary data.** Public alerts show only what is needed. Retention is short. Location sharing is consent-only.
4. **Safety over speed over features.** If a feature could get someone hurt, it does not ship until it is redesigned.
5. **Stellar only where it adds value.** Hashing, stakes, reputation, escrow and transparent funding. Not everywhere.
6. **Works on weak networks.** Offline queues, low-bandwidth mode, SMS/USSD fallback.
7. **Built in the open.** Decisions go in ADRs. Security issues get coordinated disclosure.

## Roadmap summary

| Phase | Focus | Rough duration |
|---|---|---|
| **0: Discovery** | Stakeholder interviews, legal review, publish threat model | 4 to 6 weeks |
| **1: MVP** | Telegram/WhatsApp + SMS prototype, case verification, sighting upload, responder map, testnet anchoring | ~3 months |
| **2: Community pilot** | One community or LGA, real verifiers, mainnet anchoring, stake and reputation contracts | ~3 months |
| **3: Scale** | More communities, USSD, telecom talks, anchor payouts, independent audit | Ongoing |

Full detail is in [`roadmap.md`](roadmap.md). Grant milestones map to GitHub milestones across all repos.

## Legal and compliance (to be completed in Phase 0)

Track these in `docs/legal/` as they are researched:

- Nigeria Data Protection Act 2023 (NDPA) obligations
- NCC rules on bulk or emergency messaging
- Liability for publishing location data
- Evidence handling and chain-of-custody expectations of law enforcement

> We are not lawyers. Get qualified legal review before any public launch.

## Documentation standards

- Write in plain language. Many readers are not engineers.
- One topic per file. Link instead of duplicating.
- Record significant technical decisions as ADRs in `adr/` using the format `NNNN-title.md` with *Context, Decision, Consequences*.
- Never include real case data, real phone numbers, real locations or credentials in any doc. Use clearly fake examples.
- New or changed docs go through a pull request like code.

## Contributing

Docs are the easiest way to start. Good first contributions:

- Translate alert templates and the verifier guide into Hausa, Yoruba, Igbo or Pidgin
- Review the threat model and add scenarios we missed
- Improve explanations for non-technical readers
- Draft the verifier recruitment and training guide
- Research NCC and NDPA requirements and summarise them

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for the process. Look for issues labelled `good first issue` and `docs`.

## Working with Claude Code in a Codespace

1. Open this repo in a GitHub Codespace.
2. Install and start Claude Code: `npm install -g @anthropic-ai/claude-code`, then run `claude` in the repo root. (Check Anthropic's docs for current install instructions.)
3. Add a `CLAUDE.md` in the repo root so Claude knows the rules. Suggested contents:
   - The mission and the *eyes, not fists* principle
   - "Never write real personal data or case details; use fake examples"
   - Doc style rules from the section above
   - The repo map above
4. Good first prompts:
   - *"Draft `threat-model.md` using a STRIDE-style structure for the system described in `proposal.md`."*
   - *"Write `architecture.md` with a data-flow section for case creation, sighting upload and evidence anchoring."*
   - *"Create `api/openapi.yaml` for: create case, verify case, submit sighting, list sightings for a case."*
5. Always review AI-written docs yourself. Safety-critical claims need human and expert review.

## Security

Do **not** open public issues for vulnerabilities. Follow [`SECURITY.md`](SECURITY.md).

## License

Documentation is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Add a `LICENSE` file before publishing.
