### Svår 1 – Cherry-pick + Stash

1. Skapa tre brancher:
   - `feature-login`
   - `feature-dashboard`
   - `hotfix-readme`
2. Gör 3 commits i varje branch (små, fokuserade).
3. Hämta en specifik commit från `feature-dashboard`:
   git log --oneline
   Kopiera <SHA> och cherry-picka till main:
   git switch main
   git cherry-pick <SHA>
   (Lös ev. konflikter och git cherry-pick --continue vid behov.)

4. Stasha pågående arbete i valfri branch:
   git stash push -m "temp work"
   git switch main
   git switch -c test-stash
   git stash pop

Beskriv kort i README vad som hände.

5. Skapa en loggfil:
   git log --oneline --graph --decorate --all > git-history.txt

Lägg till och committa loggen.

---

### Svår 2 – Ångra och återställa

Syfte: Förstå skillnaden mellan `reset` och `revert`.

1. Skapa ett repo och gör tre commits med olika ändringar i samma fil.
2. Kör `git log --oneline` för att se commit-historiken.
3. Använd `git reset --hard <SHA_forsta_committen>` för att backa till den första committen.
4. Återställ därefter med `git revert` för att skapa en motsats-commit.
5. Gör en sammanställning i README:
   - När ska du använda `reset`?
   - När ska du använda `revert`?
   - Vad är riskerna?

> Extra: Testa även `git restore <fil>` för att återställa enstaka filer.

---

### Svår 3 – Git-strategier & loggar (fördjupning)

Syfte: Visa att du kan navigera mellan flera brancher och förstå historiken.

1. Använd brancherna från Del 1.
2. Välj en specifik commit i feature-dashboard:
   git log --oneline
3. Cherry-picka:
   git switch main
   git cherry-pick <SHA>
   (Lös ev. konflikter.)
4. Stasha temporärt arbete i valfri branch:
   git stash push -m "Temp work"
   git switch main
   git stash pop
5. Skapa logg igen och jämför:
   git log --oneline --graph --decorate --all > git-history.txt

Tips: git log --graph --decorate --all används i examinationen för att verifiera din historik.
