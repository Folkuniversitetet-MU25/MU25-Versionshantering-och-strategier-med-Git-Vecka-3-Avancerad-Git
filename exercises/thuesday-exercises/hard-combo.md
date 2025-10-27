Titel: Kombinationsövning – Cherry-pick + Stash i teamflöde

Syfte

Tillämpa cherry-pick och stash i ett samarbetsliknande scenario: hantera akut hotfix utan att förlora eget WIP-arbete.

Scenario

Du arbetar i en branch feature/contact-form.
Du får en bugg-rapport som kräver snabb fix i main.

Steg-för-steg

1. Skapa en ny branch för din feature:

git switch -c feature/contact-form
echo "<form>Contact us!</form>" > contact.html
git add .
git commit -m "feat: add contact form"

2. Gör en halvfärdig ändring (WIP):

echo "TODO: add validation" >> contact.html
git status

(Låt ändringen vara ostaged.)

3. Du får akut buggfix att göra i main.
   Stasha ditt arbete:

git stash push -m "WIP: contact form validation"

4. Byt till main och skapa hotfix:

git switch main
echo "Fix: remove console.log" >> app.js
git add app.js
git commit -m "Hotfix: remove console.log"

5. Cherry-picka hotfixen till din feature-branch (så den finns där också):

git log --oneline -n 1
git switch feature/contact-form
git cherry-pick <SHA>

6. Återställ ditt WIP-arbete:

git stash pop

7. Kontrollera att:

Dina contact.html-ändringar finns kvar

Hotfixen är integrerad

Historiken ser ren ut (git log --oneline -n 5)

Reflektionsfrågor

Vad hade hänt om du inte stashat innan du bytte branch?

När är cherry-pick + stash en smart kombination i teamarbete?

Hur hade du dokumenterat detta i PR:n för tydlighet?
