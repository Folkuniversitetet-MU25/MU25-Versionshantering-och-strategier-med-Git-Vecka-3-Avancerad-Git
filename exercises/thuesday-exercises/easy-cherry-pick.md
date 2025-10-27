Titel: Cherry-pick en commit mellan brancher

Syfte

Träna på att ta en specifik commit från en branch och föra över den till main – utan att mergea hela grenen.

Uppgift

1. Skapa en ny branch:
   git switch -c feature-typo-fix

2. Lägg till en ny fil:
   echo "Hello Git Students!" > greetings.txt
   git add greetings.txt
   git commit -m "Add greetings.txt"

3. Gör en liten ändring (hotfix):
   echo "Hello Git Students!!!" > greetings.txt
   git add greetings.txt
   git commit -m "Fix: adjust punctuation in greetings.txt"

4. Ta fram SHA på senaste commit:
   git log --oneline -n 1

5. Gå till main och cherry-picka in committen:
   git switch main
   git cherry-pick <SHA>

6. Verifiera i loggen och med cat greetings.txt.
   Är filen uppdaterad i main utan att hela grenen följde med?

💬 Reflektionsfråga

När är cherry-pick bättre än merge i ett riktigt teamprojekt?
