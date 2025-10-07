# 04 – Stash: parkera WIP och context switch

**Mål:** Spara undan halvfärdigt arbete för att snabbt hantera en hotfix.

## Uppgift
1. På en feature-branch: ändra två filer utan att committa.
2. `git stash push -m "wip: settings ui"`
3. Byt till hotfix-branch, gör fix, merg(a).
4. Tillbaka till din feature: `git stash list` → `git stash apply` (eller `pop`).
5. Fortsätt, committa, push och öppna PR. Beskriv kort flödet du använde.

## Godkänt när
- Din stash återställs korrekt och PR:n beskriver hur du gjorde.
- **Minst 1 review** inkommen.
