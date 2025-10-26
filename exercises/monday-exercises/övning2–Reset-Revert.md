# Övning 2 – Reset vs Revert (före/efter push)

**Syfte:** Förstå skillnaden mellan lokalt “spola tillbaka bandet” (reset) och “ångra publikt” (revert).

**Viktigt:** Gör ALDRIG `reset --hard` på delad/pushad historik.

## Setup

1. Stå på main och skapa en enkel filhistorik:

   ```bash
   git switch main
   echo "v1" > notes.txt
   git add .
   git commit -m "v1"

   echo "v2" >> notes.txt
   git add .
   git commit -m "v2"

   echo "v3" >> notes.txt
   git add .
   git commit -m "v3"
   ```

Del A – Reset (före push)

Lokalt backa en commit:

git reset HEAD~1

Kolla fil och logg:

cat notes.txt # v1, v2
git log --oneline

Lärdom: Reset flyttar HEAD/branchpekaren bakåt. Historiken förändras lokalt.

Återställ till senaste igen (Valfritt):

git switch -c scratch && git switch -

# eller gör en ny commit på nytt innehåll, upp till dig

Del B – Revert (efter push)

Push aktuell historik:

git push origin main

Ångra senaste commit publikt:

git revert HEAD
git push origin main

Kolla loggen:

git log --oneline

Lärdom: Revert skapar en NY commit som “gör motsatsen”. Delad historik bevaras.

Extra – Reset --soft / --hard (lokalt)

Skapa en test-branch lokalt:

git switch -c reset-playground
echo "temp1" >> notes.txt
git add .
git commit -m "temp1"

echo "temp2" >> notes.txt
git add .
git commit -m "temp2"

Testa:

--soft (behåller staged ändringar):

git reset --soft HEAD~1
git status

--hard (kastar lokala ändringar):

git reset --hard HEAD~1
git status

OBS: Gör detta ENDAST i en lokal test-branch som inte är pushad.

Reflektion

När är revert rätt val?

Vad händer med commit-IDs (hashar) efter reset vs revert?

När är --soft praktiskt?

Klart när

Du har demonstrerat både reset (före push) och revert (efter push) samt kan förklara skillnaden.
