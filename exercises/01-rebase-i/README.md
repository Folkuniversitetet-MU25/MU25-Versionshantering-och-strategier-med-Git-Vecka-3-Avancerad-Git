# 01 – Rebase (interaktiv): städa historiken

**Mål:** Använd `git rebase -i` för att kombinera, döpa om och ordna commits så att historiken blir tydlig.

> **Arbeta i ditt eget repo.** Öppna PR i ditt repo (inte mot lärar-repot).

## Förbered (i ditt repo)
1. `git checkout -b feat/profile` från `main`.
2. Gör 4 små commits som innehåller:
   - en stavfelsfix i valfri fil (t.ex. `bio.txt`)
   - ta bort en `console.log`/onödig rad
   - en “riktig” ändring (ex. ny funktionalitet/sektion)
   - uppdatering i `README.md` (valfri text)

## Uppgift
1. `git rebase -i HEAD~4`
   - `squash`a de två småfixarna in i den “riktiga” ändringen
   - `reword`a commit-rubriken till något meningsfullt
   - låt README-committen ligga sist
2. Push och öppna PR mot `main` i **ditt** repo.  
   Har du pushat tidigare? Använd `git push --force-with-lease`.

## Checklista (självkontroll)
- [ ] Historiken visar **2 tydliga commits** (riktig ändring + README)
- [ ] PR-texten beskriver **varför** du städade historiken och **hur** du gjorde
