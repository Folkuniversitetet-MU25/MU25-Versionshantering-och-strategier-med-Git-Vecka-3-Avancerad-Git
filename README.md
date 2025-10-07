# Vecka 3 – Avancerad Git

Fokus denna vecka: **rebase (interaktiv)**, **cherry-pick**, **revert**, **stash** samt **konfliktlösning**.
Målet är att bli trygg i de vanligaste “rädda-läget”-scenarierna och att hålla historiken ren och begriplig.

> **Viktigt om upplägg:**    
> • Varje student jobbar i **eget repo** (eller eget fork) och **öppnar PR i sitt eget repo**.  
> • **Gör inte PR mot detta (lärarens) repo.** PR hit stängs utan granskning.  
> • Vill du ha feedback? Be en klasskamrat reviewa din PR i ditt repo (frivilligt).

## Snabblänkar till övningar
- [01 – Rebase (interaktiv)](exercises/01-rebase-i/README.md)
- [02 – Cherry-pick (hotfix mellan grenar)](exercises/02-cherry-pick/README.md)
- [03 – Revert (ångra säkert i delat repo)](exercises/03-revert/README.md)
- [04 – Stash (parkera WIP)](exercises/04-stash/README.md)
- [05 – Konflikt-labb (skapa & lös konflikt)](exercises/05-conflict/README.md)

## Så arbetar du
1. Skapa **ett eget repo** för vecka 3, t.ex. `mu25-v3-ditt-namn`.  
2. Skapa **en feature-branch per övning**.  
3. Följ instruktionerna i respektive övning.  
4. Öppna **en PR per övning i ditt eget repo** och använd gärna [PR-mallen](/pull_request_template.md)
5. (Frivilligt) Be **minst en klasskamrat** reviewa varje PR. Svara på feedback.
6. 5. Merg(a) när PR är godkänd (Squash & merge är OK för ren historik).

## Förutsättningar
- Git installerat och konfigurerat (`user.name`, `user.email`, `init.defaultBranch=main`)
- Autentisering mot GitHub (PAT eller SSH)
- Editor/IDE (t.ex. VS Code)

## Tips
- Commits: håll dem små och beskrivande (`feat: ...`, `fix: ...`, `docs: ...`)
- Branchnamn: `feat/rebase-labb`, `fix/login-null-check`, osv.

