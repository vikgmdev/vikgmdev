<h1 align="center">Hey, I'm Victor 👋</h1>

<p align="center">
  <strong>NestJS &amp; Kubernetes consultant · Founder at Totem Labs Forge</strong>
</p>

<p align="center">
  <em>Not a vibe coder. A senior engineer with the architecture background AI needs to actually ship something real.</em>
</p>

<p align="center">
  <a href="https://vikgmdev.com">vikgmdev.com</a> ·
  <a href="https://totemlabs.io">totemlabs.io</a> ·
  <a href="https://eraastrology.ai">eraastrology.ai</a> ·
  <a href="https://forgetty.dev">forgetty.dev</a>
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/vikgmdev"><img src="https://img.shields.io/badge/LinkedIn-vikgmdev-0A66C2?style=flat&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  <a href="https://x.com/vikgmdev"><img src="https://img.shields.io/badge/X-@vikgmdev-000000?style=flat&logo=x&logoColor=white" alt="X/Twitter"></a>
  <a href="mailto:vikgm.dev@gmail.com"><img src="https://img.shields.io/badge/Email-vikgm.dev@gmail.com-EA4335?style=flat&logo=gmail&logoColor=white" alt="Email"></a>
</p>

<p align="center">
  <sub>✨&nbsp;&nbsp;Now shipping&nbsp;&nbsp;✨</sub>
</p>

<p align="center">
  <a href="https://eraastrology.ai">
    <img src="assets/era-icon.png" alt="ERA — Cosmobiology AI" width="96" height="96" />
  </a>
</p>

<p align="center">
  <strong>ERA — Cosmobiology AI</strong><br/>
  <sub><a href="https://eraastrology.ai">eraastrology.ai</a> · three-generation lineage, live on Android</sub>
</p>

<p align="center">
  <a href="https://play.google.com/store/apps/details?id=ai.eraastrology.app">
    <img src="https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png" alt="Get it on Google Play" height="72" />
  </a>
</p>

<h2 align="center">Need a consultant?</h2>

<p align="center">
  <a href="mailto:vikgm.dev@gmail.com?subject=NestJS%20consulting%20inquiry">
    <img src="https://img.shields.io/badge/NestJS%20Expert-Migrations%20%26%20Architecture-E0234E?style=for-the-badge&logo=nestjs&logoColor=white" alt="NestJS Expert — Migrations & Architecture" />
  </a>
  &nbsp;
  <a href="mailto:vikgm.dev@gmail.com?subject=Kubernetes%20consulting%20inquiry">
    <img src="https://img.shields.io/badge/Kubernetes%20Consultant-Bare%20Metal%20%26%20GitOps-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" alt="Kubernetes Consultant — Bare Metal & GitOps" />
  </a>
</p>

---

## What I do

**A decade as a Backend Engineer first.** Node.js / TypeScript / NestJS / GraphQL / microservices — before anything else, that's the root. On top of that: years of hands-on infrastructure at bare-metal scale (Kubernetes, Ansible, Kafka, Postgres HA, Elasticsearch, Redis Cluster), and the last ~2 years going deep on AI — building MCP servers in production, running multi-agent harnesses, and shipping AI-native products end-to-end.

I run two parallel tracks today:

1. **Senior Backend / DevOps** at a blockchain security platform — platform, API, observability, on-call.
2. **Founder & sole engineer** at [Totem Labs Forge LLC](https://totemlabs.io) — a Delaware product studio where I design, build and ship AI-first products end-to-end under a custom multi-agent harness.

### Engineer first, then AI-multiplied

AI coding tools are turning a lot of people into "vibe coders" — shipping surface-level demos that fall apart the moment they hit real load, real state, or a real incident. **I'm the opposite.** I came up the hard way: wire protocols, daemon architectures, stateful migrations, SCRAM auth, pgBackRest DR, CI/CD pipelines written by hand.

Because I already know how systems work at the byte level — how a Kafka broker negotiates TLS, how a Cilium pod masquerades through a vSwitch, how a Vault AppRole round-trips a token, how `@elastic/elasticsearch` shape-drifts between v7 and v9 — I can let AI do the drudge typing while I keep ownership of the architecture. The result is not a demo. It's **~38K lines of production Rust in 24 days** ([Forgetty](https://forgetty.dev)), **an AI app live on Google Play** ([ERA](https://eraastrology.ai)) on a cost-controlled three-tier model stack, **a production MCP server**, and **a harness-driven Kubernetes cluster** that a teammate can re-stand-up in an afternoon.

AI is the multiplier. Backend + infra engineering is the foundation that lets the multiplier do anything useful.

---

## Production-grade infra — the four I run every day

This is my strongest surface. I don't "know" Kubernetes, Redis, Postgres and Elasticsearch from a course — I operate all four in production, on real traffic, with real users downstream, at the same time.

<table>
<tr>
<td width="50%" valign="top">

### <img src="https://cdn.simpleicons.org/kubernetes/326CE5" height="20" /> &nbsp; Kubernetes — production grade

Bootstrap from scratch on bare metal. Not a managed cluster, not `minikube`, not a demo.

- **kubeadm** HA control plane (3 nodes), external load-balanced API endpoint
- **Cilium eBPF** CNI with `kubeProxyReplacement: Strict`, Hubble observability, vSwitch-aware MTU
- **ArgoCD GitOps** — AppSets per environment, webhook-triggered reconciliation, zero `kubectl apply` after bootstrap
- **External Secrets Operator + Hashicorp Vault** — KV v2, AppRoles scoped per env, no secret ever in Git
- **Cloudflared Zero Trust** — no public load balancer, authenticated access only
- 10-script reproducible bootstrap. A teammate re-stands-up the cluster before the coffee cools.

</td>
<td width="50%" valign="top">

### <img src="https://cdn.simpleicons.org/redis/DC382D" height="20" /> &nbsp; Redis — Cluster + hardened

Not a cache sitting on `0.0.0.0`. Multi-instance, per-service, end-to-end hardened.

- **Redis Cluster** (multi-node) + dedicated per-service instances for isolation
- **End-to-end hardening playbook** — VLAN only, localhost-only, `protected-mode`, auth required
- Memory policies, persistence config, replication topology tuned per workload
- Role-based use: cache, rate-limiting, session / webhook storage, queue surfaces
- Federated into Prometheus; Grafana dashboards; Alertmanager paging on mem-fragment / replica-lag / evicted-keys

</td>
</tr>
<tr>
<td width="50%" valign="top">

### <img src="https://cdn.simpleicons.org/postgresql/4169E1" height="20" /> &nbsp; PostgreSQL — HA + real DR

"We have backups" is not DR. "Our restore runs every week and passes shape-compare" is DR.

- **PostgreSQL HA** with streaming replication (primary + replicas)
- **pgBackRest** local + SFTP to off-provider storage (Hetzner Storage Box)
- **Automated DR restore testing** on a dedicated restore host — we find out when DR breaks, not during an outage
- **Knex** for migrations, careful dual-write patterns for schema drift
- Role-based access, `SCRAM-SHA-256`, `pg_hba` policy per tier, tuned `checkpoint_*` / `shared_buffers` / `effective_cache_size`

</td>
<td width="50%" valign="top">

### <img src="https://cdn.simpleicons.org/elasticsearch/005571" height="20" /> &nbsp; Elasticsearch — multi-cluster + migration-proven

Drove a **major-version migration (v7 → v9) with zero regression** on a live, multi-cluster production platform.

- Multi-cluster topology (legacy + current + product-specific) — none of this is theoretical
- **Shape-compare safety net** — a utility that diffs response shape field-by-field before any service cuts over. Written in Node, wired into CI. Blocks cutover on any non-tolerated diff.
- **Per-service SPEC → Build → QA** migration — one endpoint at a time, 24h bake, reversible flip-back
- Dual-write ingestion phases, index-by-index decommission, analyzer / mapping / `_source` debugging at the byte level
- Replicas, refresh-interval, per-tier settings tuned for production (never "works on my laptop")

</td>
</tr>
</table>

**The common thread:** I know these four at the byte level — how a Redis `protected-mode` handshake rejects, how `pgBackRest` asyncs a full backup to SFTP, how Cilium masquerades pod source IPs through a vSwitch, how `@elastic/elasticsearch` drifts between v7 and v9. That's what lets me ship zero-regression migrations instead of blog posts.

---

## Products I'm shipping from Totem Labs Forge

### 🔮 [ERA — Cosmobiology AI](https://eraastrology.ai)

Live on [Google Play](https://play.google.com/store/apps/details?id=ai.eraastrology.app) since April 2026. Built on a methodology transmitted directly from Hector García — a master astrologer with 30+ years of practice, my father — so ERA reasons from a real interpretive lineage rather than "trained on data".

### 💻 [Forgetty — GTK4 Rust terminal emulator](https://forgetty.dev)

MIT on [github.com/vikgmdev/forgetty](https://github.com/vikgmdev/forgetty). Daemon-first architecture (PTY + byte-log + session persistence in the daemon; renderers own VT parsing via libghostty-vt FFI). Binary length-prefixed wire protocol. Tabs + split panes, per-pane scrollback, search, 486 bundled themes, command palette, session restore, named workspaces, socket API. **24 days / ~38K LOC of production Rust despite no prior Rust experience** — evidence that the Forge harness works: it handles the drudge typing while I own the architecture decisions.

### 🧠 Forge harness

The methodology that made Forgetty and ERA possible at solo-founder velocity. A three-phase subagent-isolated workflow:

- **Plan** — spec + acceptance criteria agent
- **Build** — implementation agent with mandatory `simplify` / `audit-rust` / `audit-security` passes
- **QA** — human-in-the-loop QA scored 1–10 on five axes, binary pass/fail

Per-task git worktrees let me run 3–5 feature sessions in parallel; overnight autonomous mode completes tasks unattended with deferred QA for the morning.

---

## Stack

#### Languages

<p>
  <img src="https://skillicons.dev/icons?i=ts,js,go,rust,solidity,bash&theme=dark" alt="Languages" />
</p>

#### Backend & APIs

<p>
  <img src="https://skillicons.dev/icons?i=nodejs,nestjs,express,graphql&theme=dark" alt="Backend" />
  &nbsp;
  <img src="https://img.shields.io/badge/MCP-Model%20Context%20Protocol-7C3AED?style=for-the-badge" alt="MCP" />
  <img src="https://img.shields.io/badge/REST-blue?style=for-the-badge" alt="REST" />
  <img src="https://img.shields.io/badge/WebSockets-010101?style=for-the-badge&logo=socket.io&logoColor=white" alt="WebSockets" />
</p>

#### Data & streaming

<p>
  <img src="https://skillicons.dev/icons?i=postgres,redis,mongodb,mysql,kafka,elasticsearch&theme=dark" alt="Data" />
  &nbsp;
  <img src="https://img.shields.io/badge/Neo4j-008CC1?style=for-the-badge&logo=neo4j&logoColor=white" alt="Neo4j" />
  <img src="https://img.shields.io/badge/ClickHouse-FFCC01?style=for-the-badge&logo=clickhouse&logoColor=black" alt="ClickHouse" />
  <img src="https://img.shields.io/badge/MinIO-C72E49?style=for-the-badge&logo=minio&logoColor=white" alt="MinIO" />
</p>

#### Platform / DevOps

<p>
  <img src="https://skillicons.dev/icons?i=kubernetes,docker,ansible,terraform,nginx,bash,linux,cloudflare&theme=dark" alt="Platform" />
  &nbsp;
  <img src="https://img.shields.io/badge/Cilium%20eBPF-F8C517?style=for-the-badge&logo=cilium&logoColor=black" alt="Cilium" />
  <img src="https://img.shields.io/badge/ArgoCD-EF7B4D?style=for-the-badge&logo=argo&logoColor=white" alt="ArgoCD" />
  <img src="https://img.shields.io/badge/Vault-000000?style=for-the-badge&logo=vault&logoColor=FFEC6E" alt="Vault" />
  <img src="https://img.shields.io/badge/Teleport-512FC9?style=for-the-badge&logo=teleport&logoColor=white" alt="Teleport" />
</p>

#### Observability

<p>
  <img src="https://skillicons.dev/icons?i=grafana,prometheus&theme=dark" alt="Observability" />
  &nbsp;
  <img src="https://img.shields.io/badge/Alertmanager-E6522C?style=for-the-badge&logo=prometheus&logoColor=white" alt="Alertmanager" />
  <img src="https://img.shields.io/badge/PagerDuty-06AC38?style=for-the-badge&logo=pagerduty&logoColor=white" alt="PagerDuty" />
</p>

#### AI / LLMOps

<p>
  <img src="https://img.shields.io/badge/Claude-D97757?style=for-the-badge&logo=claude&logoColor=white" alt="Claude" />
  <img src="https://img.shields.io/badge/Claude%20Code-D97757?style=for-the-badge&logo=anthropic&logoColor=white" alt="Claude Code" />
  <img src="https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white" alt="OpenAI" />
  <img src="https://img.shields.io/badge/DeepSeek-0A7BFF?style=for-the-badge" alt="DeepSeek" />
  <img src="https://img.shields.io/badge/MCP-7C3AED?style=for-the-badge" alt="MCP" />
</p>

#### Frontend / Mobile (product work at Totem Labs)

<p>
  <img src="https://skillicons.dev/icons?i=react,vite,tailwind,threejs,kotlin,swift&theme=dark" alt="Frontend / Mobile" />
  &nbsp;
  <img src="https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Android" />
  <img src="https://img.shields.io/badge/Capacitor-119EFF?style=for-the-badge&logo=capacitor&logoColor=white" alt="Capacitor" />
  <img src="https://img.shields.io/badge/GTK4-7B7B7B?style=for-the-badge&logo=gnome&logoColor=white" alt="GTK4" />
</p>

#### Cloud & bare metal

<p>
  <img src="https://skillicons.dev/icons?i=cloudflare&theme=dark" alt="Cloud" />
  &nbsp;
  <img src="https://img.shields.io/badge/Hetzner-D50C2D?style=for-the-badge&logo=hetzner&logoColor=white" alt="Hetzner" />
  <img src="https://img.shields.io/badge/OVH-123F6D?style=for-the-badge&logo=ovh&logoColor=white" alt="OVH" />
</p>

#### Blockchain

<p>
  <img src="https://img.shields.io/badge/Cosmos-2E3148?style=for-the-badge&logo=cosmos&logoColor=white" alt="Cosmos" />
  <img src="https://img.shields.io/badge/Stellar-000000?style=for-the-badge&logo=stellar&logoColor=white" alt="Stellar" />
  <img src="https://img.shields.io/badge/XRPL%20EVM-23292F?style=for-the-badge&logo=xrp&logoColor=white" alt="XRPL EVM" />
  <img src="https://img.shields.io/badge/Solana-9945FF?style=for-the-badge&logo=solana&logoColor=white" alt="Solana" />
  <img src="https://img.shields.io/badge/Solidity-363636?style=for-the-badge&logo=solidity&logoColor=white" alt="Solidity" />
</p>

<sub>Operator-grade experience across Cosmos · Stellar · XRPL EVM. Solana: RPC integrations and on-chain indexing (not pitched as a protocol specialist). Solidity smart-contract exposure.</sub>

---

## Hire me

Short, paid engagements for teams that want real engineering on top of AI — not the other way around.

<p>
  <img src="https://img.shields.io/badge/NestJS%20Expert-Migrations%20%26%20Architecture-E0234E?style=for-the-badge&logo=nestjs&logoColor=white" alt="NestJS Expert — Migrations & Architecture" />
  &nbsp;
  <img src="https://img.shields.io/badge/Kubernetes%20Consultant-Bare%20Metal%20%26%20GitOps-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" alt="Kubernetes Consultant — Bare Metal & GitOps" />
</p>

- **NestJS expert** — migrations _to_ NestJS from Express / Koa / vanilla Node / monolithic TS backends. Architecture, module boundaries, DI done right, GraphQL / REST / WebSockets / MCP resolvers, testing and CI/CD. Shipped large NestJS codebases in production — I know how to land the migration without freezing your feature work.
- **Kubernetes on bare metal** — bootstrap from scratch, reproducible in an afternoon. kubeadm HA control plane, Cilium eBPF, ArgoCD GitOps, External Secrets Operator + Vault, Cloudflared Zero Trust ingress, observability that actually pages the right person.
- **Elasticsearch migrations** — major-version upgrades on live platforms. Shape-compare safety net, dual-write phases, per-service SPEC → Build → QA, reversible flip-back. Zero regression is the _target_, not a wish.
- **PostgreSQL HA + real DR** — streaming replication, `pgBackRest` to off-provider storage, _automated restore testing_ so you find out DR is broken on Tuesday afternoon, not at 3am.
- **Redis — Cluster + hardening** — multi-instance topology per workload, end-to-end lockdown (VLAN + localhost + `protected-mode` + auth), Prometheus federation + paging. No more caches listening on `0.0.0.0`.
- **Kafka** — TLS + SASL/SCRAM + per-consumer ACLs, the streaming backbone without the footguns.
- **AI-multiplied engineering for your team** — how to plug Claude Code / MCP / multi-agent harnesses into your real SDLC without turning your codebase into a vibe-coded graveyard. Architecture-first, shipping-focused.

<p>
  <a href="mailto:vikgm.dev@gmail.com?subject=Consulting%20inquiry">
    <img src="https://img.shields.io/badge/📧%20Email%20me%20to%20book%20a%20call-vikgm.dev@gmail.com-F97316?style=for-the-badge" alt="Email me to book a call" />
  </a>
</p>

---

## Read

- **[vikgmdev.com](https://vikgmdev.com)** — portfolio with technical case studies
- **[Kubernetes from scratch on bare metal](https://vikgmdev.com/kubernetes-bootstrap)** — 10-script reproducible bootstrap
- **[Elasticsearch v7 → v9 migration on a live platform](https://vikgmdev.com/elasticsearch-migration)** — shape-compare strategy, zero regression

---

<p align="center">
  <sub>Profile scaffolding inspired by the open-source <a href="https://github.com/santifer/career-ops">career-ops</a> and <a href="https://github.com/santifer/cv-santiago">cv-santiago</a> by <a href="https://github.com/santifer">@santifer</a>. Thank you for the blueprint 🙏</sub>
</p>
