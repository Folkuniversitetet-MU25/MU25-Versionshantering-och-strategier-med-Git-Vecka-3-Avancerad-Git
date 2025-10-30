### Medel – PR-flöde & konfliktträning

Syfte: Simulera det flöde du ska visa på examinationen (branch → PR → review → merge).

(0. Om ni inte hinner göra detta tillsammans i par – gör en simulering själv med två brancher (student-a, student-b).)

1. Arbeta i par.
2. En student initierar ett repo och pushar till GitHub. Bjud in din klasskamrat som Collaborator.
3. Den andra klonar repot (`git clone <URL>`).
4. Båda skapar varsin branch och gör små ändringar i samma fil (t.ex. `README.md`).
5. 5. Skapa PR. Partnern lämnar review (kommentar/godkännande). Merg:a med Squash & Merge.
6. Skapa sedan en konflikt:

- Gör en ny branch feature-readme-conflict

- Ändra samma rad i `README.md` som redan ändrats i `main`.

- Öppna PR → försök merge:a → få konflikt.

- Lös konflikten lokalt eller i GitHub UI

- Skriv i PR-kommentaren hur du löste konflikten (vad/hur/varför).

7. Diskutera i paret (skriv 3–5 meningar i README):

- Hur hade denna konflikt kunnat förebyggas?
- Vad skiljer “merge” från “squash merge”? Varför är squash bättre här?
- Hur upplevde du reviews – var det lätt eller svårt att ge konstruktiv feedback?

> Tips: Använd GitHub PR-kommentarer för att dokumentera hur ni löste konflikten.
