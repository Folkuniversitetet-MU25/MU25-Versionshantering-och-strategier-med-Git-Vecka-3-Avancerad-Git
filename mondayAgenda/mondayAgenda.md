🧭 Lektion: Avancerad Git – Konflikter, Rebase, Revert & Reset

📅 Datum: Måndag 27 okt
🕐 Tid: 13:00–16:00
📚 Kurs: Versionshantering och strategier med Git (20 yhp)
🎯 Vecka: 3
👨‍🏫 Lärare: Mandus Lindström
💡 Fokus: Konflikter, merge-verktyg, ångra med Git, rebase & case-studier

---

---

🎯 Lektionsmål

Efter lektionen ska studenterna kunna:

Identifiera och lösa mergekonflikter i Git.

Använda reset, revert och rebase på ett säkert sätt.

Förstå när och varför man använder olika strategier för att ångra förändringar.

Visa förmåga att samarbeta i ett repo och hantera problem i versionshantering.

---

---

📝 Lektionsplanering (3 timmar)

– Uppstart

- Förberedelser: Rekommenderad setup före lektionen

– PowerPoint & Teori (Slides 65-83)

– Demo / Code-Along: Konflikt i realtid

- Innehåll: Läraren visar: två brancher → merge → konflikt → lösning i VS Code.
- Syfte: Se processen i praktiken.

– Demo 2 / Code-Along 2: Revert vs Reset

- Innehåll: Visa skillnad före/efter push. Visa effekten på commit-historik.
- Syfte: Förstå riskerna och rätt val av verktyg.

– Demo 3 / Code-Along 3: Mini-case: Rebase och Stash

- Innehåll:
  • Rebase i egen branch (squash, reorder)
  • Stash/unstash WIP
  • Reset vs revert case-study
- Syfte: Tillämpa avancerade Git-funktioner.

– Övningar: Studenterna jobbar i par/grupp.

- Reflektion

När väljer du revert framför reset?

Vad gör git rebase -i som merge inte gör?

Hur ser du att en konflikt är löst i git status?

Hur återhämtar du dig om något går fel? (hint: git reflog)

— — — — — — — — — — — — — — — — —

🗣️ Mikro-talktrack (lärarstöd – håll för dig själv)

• När väljer jag revert framför reset?
→ Efter push / på delad historik – bevara historik, ångra säkert.

• Vad gör `git rebase -i` som merge inte gör?
→ Städar min egen feature-branchs historia (reorder/squash/reword) innan den möter main.

• Hur ser jag att en konflikt är löst i `git status`?
→ Filer går från “both modified” → staged och `status` visar inga “unmerged paths”.

• Hur återhämtar jag mig om något går fel?
→ `git reflog` för att hitta tidigare läge → ev. `git reset --hard HEAD@{n}` (endast lokalt/opushat).

— — — — — — — — — — — — — — — — —

---

---

📢 PowerPoint – Talarmanus:

## Slide 65-83 Avancerad Git – Vecka 3 (mån 27 okt, 13:00–16:00) — start

---

### Slide 65

**Titel:** Konflikter

**Innehåll:**

En konflikt uppstår när två användare ändrar samma kodrad i olika commits.
Git vet inte vilken version som är rätt och behöver din hjälp för att lösa det.

**Talarmanus:**
En konflikt i Git är inget fel – det är en naturlig del av samarbete.
Det betyder bara att Git inte kan avgöra vilken version som ska vinna.
Två personer har ändrat samma rad eller fil samtidigt.
Vi måste manuellt välja vilka delar som ska sparas, och sedan göra en ny commit som löser konflikten.

---

### Slide 66

**Titel:** Konflikter (detaljer)

**Innehåll:**

En konflikt beror på att två användare har committat ändringar som motsäger varandra. Precis som i verkligheten är konflikter något som inträffar naturligt och som man behöver lära sig att hantera på ett klokt sätt.
Konflikter löses genom att man skapar en ny commit, som innehåller de ändringar som man vill spara från båda konflikt-committs. Om ändringarna är i olika filer löser Git konflikten automatiskt! Annars måste man tala om det själv, genom en merge.

**Talarmanus:**
Git försöker alltid lösa konflikter själv.
Om ni och en kollega jobbar i olika filer, fixar Git det automatiskt.
Men om ni redigerar samma rad i samma fil, då vet Git inte vilken som ska sparas.
Då får du själv gå in i filen och välja vilken kod som ska vara kvar.

---

### Slide 67

**Titel:** Konfliktlösning

**Innehåll:**

Så fort man gör en merge så finns risken att det uppkommer en konflikt. Men Git kan lösa flera sorters konflikter automatiskt.
Ändringar i olika filer → git löser konflikten automatiskt, behåller ändringarna i båda
Ändringar i samma fil, men på olika rader → git löser konflikten automatiskt, behåller ändringarna i båda
Ändringar i samma fil, på samma rad → git kan inte lösa konflikten utan att riskera att koden förstörs. Git behöver din hjälp för att lösa konflikten.

**Talarmanus:**
När en konflikt uppstår markerar Git det med `<<<<<<<`, `=======` och `>>>>>>>`.
Allt ovanför `=======` är din kod, och allt under är kollegans kod.
Ta bort markörerna, välj det som ska vara kvar, och gör sedan `git add` och `git commit`.
VS Code har ett grafiskt verktyg där du kan klicka på “Accept Current” eller “Accept Incoming” – använd det om du vill.

---

### Slide 68–69

**Titel:** Exempel konfliktlösning

**Innehåll:**

Git markerar en konflikt i filen:

```
<<<<<<< HEAD
width: 200px;
display: flex;
=======
width: 15em;
>>>>>>> new-branch
```

Efter att du löst konflikten blir filen t.ex.:

```
width: 15em;
display: flex;
```

**Talarmanus:**
Visa det här exemplet live om möjligt.
Förklara att HEAD representerar din aktuella branch, och `new-branch` är den du försöker mergea in.
När du väljer vilken kod som ska vara kvar, tar du bort markörerna och sparar filen.
Sen committar du din lösning – då är konflikten löst.

---

### Slide 70

**Titel:** Verktyg för konfliktlösning

**Innehåll:**

`git status` – visar om en konflikt pågår.
`git add` + `git commit` – avslutar lösningen.
`git log --oneline` – visar historiken efter merge.
Push till GitHub för att se resultatet.

**Talarmanus:**
När du har löst konflikten: kör `git status` för att verifiera.
Lägg till filerna igen med `git add`, och skapa sedan en ny commit.
Använd `git log --oneline` för att se att en merge-commit skapats.
Om du pushar till GitHub ser du nu en uppdaterad historik där merge är registrerad.

---

### Slide 71

**Titel:** Gruppövning – Arbeta med Git & GitHub

**Innehåll:**

En i gruppen initierar ett nytt repo.
Övriga klonar det via `git clone`.
Alla skapar egna brancher, gör commits och mergear.
Hantera konflikter om de uppstår.

**Talarmanus:**
Nu får ni samarbeta på riktigt!
En person skapar ett nytt repo och bjuder in resten via GitHub.
Alla klonar, skapar varsin branch, och jobbar på olika filer.
Efter några commits: försök mergea ihop allt.
Om konflikter uppstår – lös dem tillsammans.
Det här ger hands-on erfarenhet av samarbete i Git.

---

### Slide 72

**Titel:** Läs vidare

**Innehåll:**

Läs om konfliktlösning, ångra och återställa på:
[https://github.com/lejonmanen/git-instruktion#git](https://github.com/lejonmanen/git-instruktion#git)

**Talarmanus:**
Vill du fördjupa dig finns en riktigt bra guide här: [lejonmanen/git-instruktion](https://github.com/lejonmanen/git-instruktion#git).
Den visar flera metoder för att hantera mergekonflikter, reset, revert och återställning.

---

### Slide 73–76

**Titel:** Ångra med Git / Reset

**Innehåll:**

`git reset HEAD` – tar bort filer från staging.
`git reset --hard` – återställ alla filer till senaste commit.
Används försiktigt, eftersom du kan tappa arbete.

**Talarmanus:**
Ibland blir det fel – och det är okej.
Git låter dig ångra nästan allt.
Med `git reset` kan du backa till en tidigare commit.
`--soft` behåller ändringar, `--hard` kastar bort dem.
Visa skillnaden live så de ser hur working directory påverkas.

---

### Slide 77–81

**Titel:** Revert – Ångra på säkert sätt

**Innehåll:**

`git revert HEAD` – skapar en ny commit som tar bort effekten av den senaste.
Fungerar även för äldre commits.
Bra när du redan pushat till GitHub.

**Talarmanus:**
Till skillnad från `reset`, som ändrar historiken, skapar `revert` en ny commit som gör motsatsen till en gammal.
Det gör `revert` säkert att använda även på brancher som redan pushats.
Visa hur en revert skapar en ny commit med texten “Revert: <originalmeddelande>”.
Detta är standardmetoden i team för att ångra något offentligt.

---

### Slide 82

**Titel:** Övning – Ångra och Revert

**Innehåll:**

Skapa ett nytt repo.
Gör tre commits.
Använd `git reset` för att backa lokalt, och `git revert` för att ångra publikt.
Undersök historiken med `git log`.

**Talarmanus:**
Nu får ni träna på att ångra.
Skapa ett nytt repo, gör några commits, och testa skillnaden mellan `reset` och `revert`.
Reset är som att spola tillbaka bandet – revert är som att spela in en ny scen där du rättar till misstaget.
Se till att ni förstår vad som händer i loggen efter varje kommando.

---

### Slide 83

**Titel:** Läs vidare

**Innehåll:**

Fördjupning:
[https://github.com/lejonmanen/git-instruktion#git](https://github.com/lejonmanen/git-instruktion#git)

**Talarmanus:**
Det är en sammanställning av alla Git-kommandon vi använt hittills.
Perfekt att spara som referens när ni jobbar i riktiga projekt.

---

---

Förberedelser: Rekommenderad setup före lektionen

Det här är inställningar i Git som hjälper dig och studenterna att slippa vanliga problem.

# 1. Se till att Git inte försöker rebase automatiskt vid pull.

# Vi vill hålla det enkelt för nybörjare → merge istället.

git config --global pull.rebase false

# 2. Gör så att rebase automatiskt placerar "fixup!" och "squash!" commits rätt.

# Det här hjälper när man kör interaktiv rebase (senare i lektionen).

git config --global rebase.autosquash true

# 3. Hanterar radbrytningar mellan Windows/Mac/Linux.

Välj EN av dessa:

# (Windows) undvik CRLF/LF-strul i diffar

git config --global core.autocrlf true

# (macOS/Linux) behåll LF, konvertera input

git config --global core.autocrlf input

# 4. Kolla att Git funkar.

git --version

💡 Varför:
Dessa rader ger en stabil, förutsägbar miljö inför lektionen – så att git pull inte oväntat rebasar, och VS Code inte visar diffar p.g.a. radbrytningar.

---

---

🆘 Panik-knappar / Återhämtning i Git

Detta visar du när något går fel (t.ex. någon fastnar i rebase eller merge).

---

# Avbryt pågående operation:

git merge --abort
git rebase --abort
git cherry-pick --abort

---

Om du vill backa till föregående tillstånd:

# Visa hela historiken över var HEAD pekat (alla tillstånd)

git reflog

# Återställ till hur det såg ut före senaste operationen # Endast lokalt! Använd inte på pushad kod.

git reset --hard HEAD@{1}

---

💬 Förklaring:

merge --abort → stoppar en misslyckad merge.

rebase --abort → avbryter en rebase och återgår till utgångsläget.

cherry-pick --abort → samma sak för cherry-pick.

reflog → visar hela din historik, även “osynliga” tillstånd.

reset --hard HEAD@{1} → flyttar dig tillbaka till hur det såg ut innan allt strulade (men raderar ej-pushat arbete).

---

---

💻 Code-Along/Demo:

🧱 1. Förbered miljön (endast en gång)

I terminalen i VS Code (Ctrl + ö):

git status

👉 Kontrollera att du står på main
Om inte:

git switch main

Uppdatera till senaste versionen (om ni är flera):

git pull

---

⚙️ Konflikt & merge

Mål: Skapa och lösa en konflikt.

# 1) Skapa basfilen på main

mkdir -p 01-konflikter-reset-revert
echo ".box { width: 300px; }" > 01-konflikter-reset-revert/index.css
git add 01-konflikter-reset-revert/index.css
git commit -m "Base: index.css width 300px on main"

# 2) Skapa feature-branch och ändra samma rad

git switch -c feature-konflikt-demo
echo ".box { width: 200px; }" > 01-konflikter-reset-revert/index.css
git add 01-konflikter-reset-revert/index.css
git commit -m "Feature: index.css width 200px"

# 3) Tillbaka till main och mergea in → konflikt

git switch main
git merge feature-konflikt-demo

# --> VS Code visar konfliktmarkörer i index.css

# <<<<<<< HEAD (din, 300px)

# =======

# >>>>>>> feature-konflikt-demo (200px)

Lösning & avslut:

# Lös i VS Code (Accept Current / Incoming / Both eller manuellt)

git add 01-konflikter-reset-revert/index.css
git commit -m "Resolve merge conflict (index.css width)"

# Snabb koll:

git log --graph --oneline --decorate

# → ska visa en merge-commit

# Om det låser sig:

git merge --abort

---

🔁 Code-Along 2: Reset (före push) vs Revert (efter push)

📝 Notis:
reset ändrar historiken (lokalt) → använd före push.
revert skapar en ny “anti-commit” → använd efter push.

Startläge: Stå kvar på main.

Arbetskatalog: ren

A) RESET (före push):

# Skapa två commits

echo "Rad 1" > notes.txt
git add notes.txt
git commit -m "Add first line"

echo "Rad 2" >> notes.txt
git add notes.txt
git commit -m "Add second line"

# Backa lokalt 1 commit (förklara att historiken skrivs om lokalt)

git reset HEAD~1

# Visa resultat

type notes.txt # Windows: 'type' (eller 'cat' om du har)
git log --oneline

B) REVERT (efter push):

# Push krävs för att visa revert på delad historik

git push origin main

# Se till att arbetskatalogen är ren:

git status

# Om "modified": spara eller kasta:

# git restore --source=HEAD -- notes.txt

# eller

# git stash push -m "temp before revert"

# Revertar senaste commit (skapar en ny “anti-commit”)

git revert HEAD
git push origin main

git log --oneline -n 3 # → visar "Revert ..."

Om det låser sig:

# Om lokala ändringar stoppar revert:

git restore --source=HEAD -- notes.txt

# kasta ändr.

# eller:

git stash push -m "temp"

# ...sen

git stash pop

---

---

🔄 Code-Along 3: Rebase (interactive) & Stash

Startläge:

Branch: main

Arbetskatalog: ren

Steg:

# 1) Skapa feature-branch och tre commits

git switch -c feature-rebase-demo
echo "A" > rebase.txt
git add rebase.txt
git commit -m "First"

echo "B" >> rebase.txt
git add rebase.txt
git commit -m "Second"

echo "C" >> rebase.txt
git add rebase.txt
git commit -m "Third"

# 2) Interaktiv rebase på dina 3 commits

git status

# måste vara ren (annars: git stash push -m "wip")

git rebase -i HEAD~3

# Mini-guide i editorn (VS Code / GitLens):

Ändra raderna i listan:

pick First → reword (byt meddelande)

pick Second → squash (in i Third)

pick Third → pick

Klicka Start Rebase (GitLens) eller spara & stäng filen.

När commit-meddelanderuta öppnas: skriv nytt → spara & stäng.

Vid konflikt: lös i VS Code → git add <fil> → git rebase --continue.

Koll:

git log --oneline

# → färre commits och/eller nya meddelanden

# STASH-exempel (visa snabbt):

echo "Oavslutad kod" >> rebase.txt
git stash push -m "Work in progress"
git stash list
git stash pop

# Om det låser sig:

git rebase --abort

# Börja om:

git status
git rebase -i HEAD~3

---

Två vanliga hinder (och enkla fixes)

“Waiting for your editor to close the file…”
→ Spara & stäng commit-meddelandefönstret / TODO-fliken.
(Git väntar på att du ska bekräfta meddelandet.)

“You have unstaged changes” (rebase) / “Your local changes would be overwritten” (revert/checkout)

→ Gör arbetskatalogen ren:

git restore .
git clean -fd

# varning: tar bort otrackat

# eller spara:

git stash push -m "wip"

---

---

🧠 Övningar från slide 71 och 82 samt så finns också fler i exercises mappen
