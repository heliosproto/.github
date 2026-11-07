# Helios Protocol

**A Stellar wallet where the smart account is the identity, not a bolt-on.**

Passkey login, session keys, social recovery, sponsored transactions, and a plugin architecture for composable account policies. Open source. Apache 2.0.

[![Live demo](https://img.shields.io/badge/live_demo-heliosproto.vercel.app-ec4899?style=for-the-badge)](https://heliosproto.vercel.app) [![Factory on testnet](https://img.shields.io/badge/factory-live_on_testnet-000000?style=for-the-badge&logo=stellar&logoColor=white)](https://stellar.expert/explorer/testnet/contract/CDF4P7N4QGYOH4NYSTJR4SJFE5SQXGD2LXSNBQWMI5MOS35KLCNUGU2S) [![License](https://img.shields.io/badge/license-Apache_2.0-1f6feb?style=for-the-badge)](https://github.com/heliosproto/heliosproto/blob/main/LICENSE)

## What works today

A user can land on the demo, enroll a passkey, and watch their smart-account deploy on Soroban testnet with the session-keys plugin already installed. End to end, no seed phrase, no G-address.

- **Passkey enrollment.** WebAuthn ceremony via `/app/onboard`, credentials persisted client-side.
- **Deterministic deployment.** A factory contract derives the C-address from the credential ID and deploys the smart-account on testnet in a single call. `predict_address` and `deploy_account` return the same value, proven on-chain.
- **Plugin-wired at creation.** Every deployed account is initialized with a session-keys plugin, so session-key auth can be enforced the moment the account exists. No post-deployment setup step.
- **Verifiable on-chain.** Factory `CDF4P7N4...` and session-keys `CCT6CXG...` are live on Soroban testnet. Deploy metadata (contract IDs, WASM hashes) is committed under `contracts/deployments/testnet.json`.

[Open the live demo](https://heliosproto.vercel.app) · [View the factory on Stellar Lab](https://lab.stellar.org/r/testnet/contract/CDF4P7N4QGYOH4NYSTJR4SJFE5SQXGD2LXSNBQWMI5MOS35KLCNUGU2S) · [View the session-keys plugin](https://lab.stellar.org/r/testnet/contract/CCT6CXGBMVTCN62JDEIU5O3SXJI3R7KTWOPC5F2MSGINCTPUYXKKURNH)

## Why Helios

Every Stellar wallet today treats smart accounts as a bolt-on. Users get a classic G-address, juggle a seed phrase, sign everything manually, and lose their funds if they lose the phrase.

Helios flips it. The smart account *is* the wallet. That unlocks four things classic wallets structurally cannot do:

- **No seed phrase.** Passkeys replace them. Face ID, Touch ID, or a security key.
- **No single point of failure.** Guardians can rotate your signer if your passkey is lost.
- **No approval fatigue.** Session keys let a dApp transact within rules you set once.
- **No gas anxiety.** A paymaster covers fees so users transact before they ever hold XLM.

## What's shipping

| Area | Where it lives | Status |
|---|---|---|
| Smart-account contracts | `contracts/smart-account`, `contracts/factory`, `contracts/plugins/session-keys` | Live on testnet, plugin-wired factory ready |
| Web wallet | `web/app` (Next.js 15, Tailwind 4, shadcn/ui) | Onboard flow live, dashboard + send in progress |
| Backend services | `backend/` (FastAPI, Postgres, Redis) | Indexer + relayer MVP under construction |
| SDKs | TypeScript + Python | Scaffold |

Component-level status lives in [heliosproto/ROADMAP.md](https://github.com/heliosproto/heliosproto/blob/main/ROADMAP.md). Architecture rationale and open design questions in [heliosproto/ARCHITECTURE.md](https://github.com/heliosproto/heliosproto/blob/main/ARCHITECTURE.md).

## Get involved

Helios is open source. Contributor rewards flow through [Grantfox](https://grantfox.xyz) and the [Drips Wave for Stellar](https://www.drips.network/wave/stellar). Contributors are compensated in USDC per merged PR.

- Looking for a `good-first-issue`? [Browse open issues](https://github.com/heliosproto/heliosproto/issues?q=is%3Aissue+is%3Aopen+label%3Agood-first-issue)
- New here? Read [CONTRIBUTING.md](https://github.com/heliosproto/heliosproto/blob/main/CONTRIBUTING.md)
- Want the full architecture tour? [ARCHITECTURE.md](https://github.com/heliosproto/heliosproto/blob/main/ARCHITECTURE.md)
- Found a vulnerability? [SECURITY.md](https://github.com/heliosproto/heliosproto/blob/main/SECURITY.md)

## Stack

`Rust` · `Soroban` · `TypeScript` · `Next.js 15` · `Tailwind 4` · `Python` · `FastAPI` · `Postgres`

Three pillars (contracts, web, backend), three stacks. Pick the one you know and contribute in your own discipline.

## License

[Apache 2.0](https://github.com/heliosproto/heliosproto/blob/main/LICENSE). Everything we ship.
