# 05 – Konflikt-labb: skapa & lös en konflikt

**Mål:** Medvetet skapa en mergekonflikt och lösa den korrekt.

## Förbered
1. Skapa (om den inte finns) filen `bio.txt` med en rad: Favorite color: blue
2. Skapa två branches:
- `feat/change-color-a` som ändrar raden till `Favorite color: green`
- `feat/change-color-b` som ändrar raden till `Favorite color: red`

## Uppgift
1. Merg(a) `feat/change-color-a` till `main`.
2. Försök merg(a) `feat/change-color-b` till `main` → du får konflikt.
3. Öppna filen och lös konflikten (välj en av raderna eller skapa en kompromiss).
4. `git add` → `git commit` för att slutföra merge.
5. Öppna PR och skriv i kommentaren **hur** du resonerade (vad behölls, varför).

## Godkänt när
- Konflikten är korrekt löst och beskrivs i PR-kommentaren.
- **Minst 1 review** inkommen.
