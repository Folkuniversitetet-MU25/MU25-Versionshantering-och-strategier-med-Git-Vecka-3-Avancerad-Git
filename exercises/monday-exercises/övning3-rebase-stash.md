# Övning 3 – Rebase (interactive) & Stash

**Syfte:** Lära dig rensa upp din egen feature-historik med `git rebase -i` samt parkera arbete med `git stash`.  
**Regel:** Rebase endast **din egen** branch (inte delad main).

## Del 1 – Interaktiv rebase på egen branch

1. Skapa branch och tre commits:

   ```bash
   git switch -c feature/rebase-lab
   echo "A" > rebase.txt
   git add .
   git commit -m "Add A"

   echo "B" >> rebase.txt
   git add .
   git commit -m "Add B"

   echo "C" >> rebase.txt
   git add .
   git commit -m "Add C"
   ```

Starta interaktiv rebase:

git rebase -i HEAD~3

I editorn:

Byt ordning (flytta raderna)

squash ihop två commits

reword ett meddelande

Avsluta rebase:

git rebase --continue
git log --oneline

Mål: Historiken är städad (färre, tydligare commits).

Del 2 – Stash WIP

Lägg pågående ändring:

echo "WIP line" >> rebase.txt

Parkera arbetet:

git stash push -m "rebase-lab WIP"
git stash list

Byt branch (simulera snabb fix):

git switch main

# gör inget, switcha tillbaka

git switch feature/rebase-lab

Ta tillbaka arbetet:

git stash pop

Hantera ev. små konflikter och committa.

Extra – Rebase ovanpå uppdaterad main

Uppdatera main och rebasea om din feature:

git switch main
git pull
git switch feature/rebase-lab
git rebase main # “replay” din branch ovanpå ny main

Lös ev. konflikter → git add → git rebase --continue.

Reflektion

Varför rebase på egen branch innan PR?

När är merge bättre än rebase?

När hjälper stash dig mest?

Klart när

Din feature-branch har snygg, linjär historik och du kan förklara vad som hände.

---
