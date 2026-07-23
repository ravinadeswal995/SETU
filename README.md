# Setu

Bridge native USDC across chains into Arc, and swap on arrival — in one transaction.

**Live:** https://setu-coral.vercel.app

---

## What it does

Setu uses Circle's Cross-Chain Transfer Protocol (CCTP) to move **native** USDC into Arc:
USDC is burned on the source chain, Circle attests the burn, and fresh Circle-issued USDC is
minted on Arc. A CCTP V2 hook then routes that USDC into the asset the user actually wants —
all inside the same flow.

No wrapped tokens. No locked bridge pool. No manual claim step on the far side.

## Why this approach

- **Native, not wrapped** — the user receives Circle-issued USDC, not a bridge IOU.
- **No honeypot** — burn-and-mint means there is no standing pool of locked funds to drain.
- **One transaction** — `hookData` wires the destination mint straight into a swap.

## Stack

- Solidity — bridge router and on-Arc receipt contract
- TypeScript / JavaScript — frontend
- Circle CCTP V2 — the cross-chain rail
- Arc Testnet — chain ID `5042002`, USDC as gas

## Status

- [x] Landing page with interactive flow preview
- [ ] Wallet connect + Arc network switching
- [ ] Bridge router + on-Arc receipt contract
- [ ] CCTP V2 hook → Arc swap integration
- [ ] Live testnet demo (real burn & mint)
- [ ] External review, then mainnet

The demo on the live site is a **simulated preview**. No real funds move and no live
contracts are called yet. This checklist is the honest state of the build.

## Build in public

Every contract, decision, and dead end goes public here. Progress notes and CCTP explainers
(in Hinglish) are posted at [@ravinasachin20](https://x.com/ravinasachin20).

## Disclaimer

Setu is an independent community project running on Arc testnet. It is not affiliated with,
endorsed by, or operated on behalf of Circle. Nothing here is financial advice.
