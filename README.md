# aion2-glass-meter

A transparent, local DPS meter for **Aion 2**. No Npcap, no installer, and your data never leaves your PC.

> ⚠️ Early development. There is no working build yet. See the plan in [docs/plan.md](docs/plan.md) and the protocol research in [docs/research.md](docs/research.md) (both in Ukrainian for now).

## What it does

- Passively reads a copy of the game's network traffic using built-in Windows APIs (raw socket / Pktmon).
- Calculates damage, DPS and per-skill breakdowns for you and your party.
- Saves fight results to files on your PC.

## What it does NOT do

- Install drivers or third-party software (Npcap, WinPcap, etc.).
- Touch the game process: no memory reading, no injection, no packet modification.
- Send fight data anywhere. The only possible network request is an optional character profile lookup on the official `aion2.plaync.com` site. It is off by default.

## Why it needs administrator rights

Windows only lets administrators listen to raw network traffic. The meter keeps the TCP packets of the game's port and drops everything else immediately.

## Verifying a release

Releases are built by GitHub Actions, not on anyone's PC. Each release ships with a SHA-256 checksum and a build provenance attestation:

```bash
gh attestation verify aion2-glass-meter.exe --repo jaaguaar/aion2-glass-meter
```

## Risks

NCSoft has not officially allowed third-party meters. This project keeps the risk low (passive reading only, nothing is published), but we cannot guarantee you won't be sanctioned. Use at your own discretion.

## License

[GPL-3.0](LICENSE). You may copy and modify the code, but any version you distribute must also be open source under the same license.

This project is not affiliated with NCSoft. Aion is a trademark of NCSoft Corporation.
