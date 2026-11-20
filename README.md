# Orbital Mass

Strategy orbital RTS with a real crypto economy.

High-level point-and-click orders. An N-body physics engine (style of system_creator / nbody-raycaster / meridian) resolves motion, gravity, and line-of-sight. Authoritative checkpoints of ownership and state go on-chain. Deposits of BCH (or CashTokens) create mass claims; capturing another player’s mass transfers the claim; withdrawal redeems the underlying value to a wallet.

## Current prototype

`index.html` is a self-contained browser demo:

- Two local players (A / B) with mass from mock deposits
- Click your ship, then click a destination (high-level order)
- Continuous N-body integration client-side
- Checkpoint button emits a compact state root (the thing that would be committed on-chain)
- Mock deposit buttons add more mass claims

Open `index.html` in a browser (or host the repo on GitHub Pages).

## Architecture sketch

- **Client**: full sim + ray queries + travel view (graphics off-chain)
- **On-chain (BCH CashTokens preferred)**: deposit covenants issue mass-claim tokens; checkpoints commit ownership + compact state; withdrawal burns/redeems claims against the deposit wallets
- **Optional finer timescale**: own chain or L2 for denser checkpoints while value stays in BCH wallets

## Next

- Real CashToken deposit/withdraw flow
- Multiplayer sync (WebRTC or similar)
- Capture resolution rules that transfer claims
- Proper fixed-point determinism for checkpoint agreement

Based on patterns from blakelapierre/system_creator, nbody-raycaster, and meridian.
