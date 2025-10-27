Titel: Stash pendling – parkera WIP, gör fix, återuppta

Syfte

Förstå hur git stash används för att tillfälligt spara halvfärdigt arbete (WIP) vid branchbyte.

Uppgift

1. Gå till en ny branch:

git switch -c wip-notes-demo

2. Skapa en ny fil med text:

echo "Todo: Refactor login flow" > todo.txt
echo "Idea: New navbar design" >> todo.txt
git status

3. Stasha arbetet med ett tydligt meddelande:

git stash push -m "WIP: notes and navbar ideas"

4. Kontrollera att den finns sparad:

git stash list
git stash show -p stash@{0}

5. Hoppa till main och gör en mini-fix:

git switch main
echo "Update docs" >> README.md
git add README.md
git commit -m "Docs: update readme"

6. Gå tillbaka till din WIP-branch:

git switch -
git stash pop

7. Kontrollera att dina todo-rader är tillbaka.

cat todo.txt
git status

Reflektionsfråga

Varför är det viktigt att alltid använda -m när man staschar?
