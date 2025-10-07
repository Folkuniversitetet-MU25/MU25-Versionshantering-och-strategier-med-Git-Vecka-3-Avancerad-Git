# 01 – Rebase (interaktiv): städa historiken

**Mål:** Använd `git rebase -i` för att kombinera, döpa om och ordna commits så att historiken blir tydlig.

## Förbered
1. Skapa branch `feat/profile` från `main`.
2. Gör 4 små commits som innehåller:
   - en stavfelsfix i en fil (t.ex. `bio.txt`)
   - ta bort en `console.log`/onödig rad
   - en “riktig” ändring (ex. ny funktionalitet i filen)
   - uppdatering i `README.md` (valfri text)

## Uppgift
1. Kör `git rebase -i HEAD~4`.
2. I editorn:
   - `squash`a de två småfixarna in i den “riktiga” ändringen
   - `reword`a commit-rubriken till något meningsfullt
   - låt README-committen ligga sist
3. Push och öppna PR mot `main`.
   - Om du redan pushat tidigare och ändrat historiken lokalt: `git push --force-with-lease`.

## Godkänt när
- Historiken visar **2 tydliga commits** (en för “riktig ändring”, en för README).
- Din PR beskriver **varför** du städade historiken och **hur** du gjorde.
