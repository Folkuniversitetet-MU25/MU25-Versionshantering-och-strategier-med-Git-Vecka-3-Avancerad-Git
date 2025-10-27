🧭 Lektion: Avancerad Git – Cherry-pick, Stash & Konfliktstrategier

📅 Datum: Tis 28 okt
🕐 Tid: 13:00–16:00
📚 Kurs: Versionshantering och strategier med Git (20 yhp)
🎯 Vecka: 3
👨‍🏫 Lärare: Mandus Lindström

---

---

🎯 Lektionsmål

Cherry-pick

- Förklara när cherry-pick är bättre än merge, och genomföra git cherry-pick <SHA> säkert (inkl. lösa ev. konflikter och använda --continue/--abort).

Stash

- Använda git stash push -m, list, show -p, apply/pop för att tillfälligt parkera arbete och återuppta det vid branchbyte.

Samarbetsvana

- Dokumentera vad som hände och varför i en PR-kommentar (t.ex. vid konfliktlösning eller cherry-pick), så att teamet kan följa historiken.

---

---

📝 Lektionsplanering (3 timmar)

– Uppstart

– PowerPoint & Teori (Slides 85-93)

- PowerPoint-del 1: Cherry-pick (slides 85–86, 93)

- PowerPoint-del 2: Stash (slides 87–89)

- PowerPoint-del 3: Konfliktstrategier (slides 90–92)

– Demo / Code-along: Cherry-pick (hotfix från en separat branch till main)

– Demo 2 / Code-along: Stash pendling (parkera WIP → snabb fix → återuppta)

- Självständig övningar: Från power pointen slide 89 och 91 samt så finns också fler i exercises mappen (de lätt - medel - svår, som skapats)

– Reflektion & Q&A

Gruppdiskussion:
– När är cherry-pick bättre än merge?
(– När är det olämpligt att använda cherry-pick?)
– När ska man stash:a istället för commit:a?
(– Hur kan stash missbrukas eller skapa förvirring i ett team?)
– Hur hanterar man konflikter i team utan stress?
(– Vad är viktigast att dokumentera vid konfliktlösning?)
(– Hur kan man förebygga konflikter i större team?)

---

---

📢 PowerPoint – Talarmanus:

## Slide 84-94 Avancerad Git – Vecka 3 (tis 28 okt, 13:00–16:00) — start

---

### Slide 85

**Titel:** Cherry-pick – vad & när,

**Innehåll:**

Plocka enstaka commit(ar) från en gren till en annan utan att mergea allt.
Vanligt användningsfall: hotfix in i main + tillbaka-portning till releasegren.
Risk: dubletter/konflikter om samma rad ändras på flera ställen.

**Talarmanus:**
Cherry-pick används när du vill ta en eller flera specifika commits från en gren och lägga dem i en annan – utan att mergea hela grenen.
Det är perfekt för små, akuta ändringar – till exempel en hotfix som snabbt måste in i `main`, men också ska till nästa release-branch.
Var försiktig – samma rad kan finnas i flera brancher, vilket riskerar konflikter eller dubbletter.
Kort sagt: cherry-pick = kirurgiskt precis versionshantering.

---

### Slide 86

**Titel:** Cherry-pick – kommandon

**Talarmanus:**
Börja med att lista commits med `git log --oneline`.
När du hittat rätt commit-ID (SHA), plocka in den med `git cherry-pick <SHA>`.
Vill du ta flera commits i rad, använd `git cherry-pick A^..C` – då följer hela kedjan med.
Om en konflikt uppstår: lös, kör `git add .`, och fortsätt med `git cherry-pick --continue`.
Om du ångrar dig: `git cherry-pick --abort` avbryter processen helt.

---

### Slide 87

**Titel:** Stash – varför & när

**Talarmanus:**
Stash är som att pausa sitt arbete mitt i allt.
Du “parkerar” dina ofärdiga ändringar tillfälligt för att kunna byta branch, fixa något akut och sedan återgå.
Exempel: du jobbar på en feature, men måste snabbt hoppa till `main` för att göra en buggfix – `git stash` räddar dig.
Det är också nödvändigt ibland när du behöver köra `git pull` men har orenade filer i arbetskatalogen.

---

### Slide 88

**Titel:** Stash – kommandon

**Talarmanus:**
`git stash push -m "WIP: ..."` sparar ditt arbete med ett meddelande (“Work In Progress”).
Se vad du staschat med `git stash list`.
Vill du kika på innehållet? `git stash show -p stash@{0}`.
Återställ med `git stash apply` – då behåller du stashen – eller `git stash pop` för att ta bort den samtidigt.
Behöver du bara en fil från stashen? Använd `git checkout stash@{0} -- path/to/file`.

---

### Slide 89

**Titel:** Övning: stash pendling

**Talarmanus:**
Nu ska ni träna på att använda stash för att pendla mellan brancher.
Gör ändringar i två filer, stasha med ett tydligt meddelande, byt branch och gör en mini-fix.
Gå tillbaka och kör `git stash pop` – kolla att inga diffs återstår i `git status`.
Syftet är att förstå hur stash kan rädda dig från att tappa arbete vid snabba branchbyten.

---

### Slide 90

**Titel:** Konfliktstrategier – fördjupning

**Talarmanus:**
Konflikter kan vara av flera typer – t.ex. samma rad, rename vs edit, eller delete vs edit.
Grundregeln: innan du pushar kan du städa historiken (rebase -i), men efter push bör du använda `revert`.
VS Code har merge-verktyg där du kan välja “Accept current”, “Accept incoming” eller båda.
Kom ihåg att alltid köra appen eller tester lokalt efter varje konfliktlösning.
Målet är att förstå vad som faktiskt ändrats – inte bara att få bort varningsrutan.

---

### Slide 91

**Titel:** Konflikt-labb (styrt)

**Talarmanus:**
Här ska ni medvetet skapa en konflikt.
Skapa två brancher, ändra samma rad i båda, och försök mergea ihop.
Git kommer att markera konflikten – lös den i editorn och gör en ny commit.
Dokumentera i pull request-kommentaren vad som krockade, hur ni löste det och varför.
Det är så ni tränar på verkliga scenarioer som händer i riktiga team.

---

### Slide 92

**Titel:** Vanliga misstag & tips

**Talarmanus:**
Om du cherry-pickar på fel branch – ingen fara. Kör `git reset --hard HEAD~1` om du inte pushat än.
Om du staschar utan meddelande kan det bli kaos – skriv alltid `-m "WIP: ..."` och rensa gamla med `git stash drop`.
Vid långa konfliktkedjor – ta pauser, kör `git diff`, lös i små steg och testa lokalt ofta.
Små commits och frekventa pushes minskar risken för krångliga konflikter.

---

### Slide 93

**Titel:** Cherry-pick – repetition

**Talarmanus:**
Cherry-pick är ett avancerat men kraftfullt verktyg.
Tänk på det som “punktplockning” av commit-historik.
Det används ofta för att flytta en buggfix från en utvecklingsgren till `main`, eller för att backporta ändringar till äldre versioner.
Men: var noga med att dokumentera när du gör det – annars blir historiken svår att följa.

Praktisk jämförelse – merge vs cherry-pick

Merge för över hela grenens historik – perfekt för sammanslagning av features.
Cherry-pick däremot är selektiv – du väljer exakt vilka commits som ska med.
Ett tips: använd cherry-pick sparsamt, och bara när merge inte är rimligt.
Annars kan du snabbt skapa komplexa historiker med överlappande commits.

---

---

💻 Code-Along/Demo:

Demo 1 – Cherry-pick (hotfix från en separat branch till main)

- Branch: thuesday-28-oct-Cherry-pick-Stash-Konfliktstrategier

- Mål: Flytta en hotfix-commit från separat branch till main utan att mergea allt.

- Talarmanus
  “Nu visar jag hur cherry-pick låter mig plocka en specifik commit från en gren till en annan – perfekt för en liten hotfix som ska in snabbt i main utan att jag drar med hela branchens historik.”

- Steg (du kör – klassen följer):

# 1) Visa nuläget

git status
git branch
git log --oneline --decorate --graph -n 5

# 2) Gå till din arbetsbranch

git switch thuesday-28-oct-Cherry-pick-Stash-Konfliktstrategier

# 3) Skapa demo-mapp + hotfix-commit

mkdir -p demo
echo "export const TAX_RATE = 0.25;" > demo/config.js
git add demo/config.js
git commit -m "Add baseline config.js (TAX_RATE 25%)"

# Hotfix: rätta ett 'fel' (simulerat)

echo "export const TAX_RATE = 0.20;" > demo/config.js
git add demo/config.js
git commit -m "Hotfix: correct TAX_RATE to 20%"

# 4) Ta SHA:t för hotfixen

git log --oneline -n 1

# Kopiera SHA (ex: abc1234)

# 5) Cherry-picka till main

git switch main
git cherry-pick <SHA>

# Vid konflikt (osannolikt här): lös i editor -> git add . -> git cherry-pick --continue

# 6) Verifiera

git log --oneline --decorate -n 3
git diff # bör vara tomt direkt efter cherry-pick

- Checkpoints:

“Ser ni att bara DEN committen kom med i main, inte hela grenens commit historik?”

“Notera commit-meddelandet – dokumentera att det var en cherry-pick i PR-texten, så blir historiken begriplig.”

- Fallgropar & fix:

Cherry-pickade på fel branch? git reset --hard HEAD~1 (om ej pushat) och börja om.

Flera commits i rad? git cherry-pick A^..C (sammanhängande spann).

---

💻 Demo 2 – Stash pendling (parkera WIP → snabb fix → återuppta)

- Mål: Visa hur git stash räddar dig när du snabbt måste byta branch mitt i arbete.

- Talarmanus
  “WIP = Work In Progress – ofärdiga ändringar som inte hör hemma i en commit ännu (t.ex. halv kod, anteckningar, experiment). git stash fungerar som en pausknapp: jag parkerar WIP, hoppar till annan branch, gör en snabb fix, och återupptar där jag var. Det minskar risken för halvfärdiga commits och konflikter.”

- Steg:

# 1) Skapa/byt till en arbets-branch för WIP

git switch -c wip-stash-demo

# 2) Skapa lite WIP

echo "TODO: fyll på detaljer" >> demo/notes.md
git status # visar 'modified' (inte staged)

# 3) Stasha med tydligt meddelande

git stash push -m "WIP: notes utkast inför lektion"

# 4) Kolla stashen

git stash list
git stash show -p stash@{0} # visa diff i stashen

# 5) Snabbfix på main

git switch main
echo "tiny fix" >> README.md
echo "Fix: document cherry-pick in README" >> README.md
git add README.md
git commit -m "Docs: add cherry-pick note"

# 6) Tillbaka till där vi var och återuppta WIP

git switch - # '-' hoppar tillbaka till föregående branch
git switch - thuesday-28-oct-Cherry-pick-Stash-Konfliktstrategier
git stash pop # eller: git stash apply (behåller stashen)

# Vid ev. konflikt -> lös, git add ., fortsätt

# 7) Kontroll

git status # WIP ska vara tillbaka
cat demo/notes.md (Windows: type demo\notes.md)

- Checkpoints:

“Viktigt: alltid ett -m meddelande i stash push, annars blir listan kaotisk.”

“Ni ska inte ha diffs kvar efter pop + ev. fix.”

“pop tar bort stashen, apply behåller – välj efter behov.”

- Fallgropar & fix:

Krock/Konflikt vid pop? Lös konflikten (i editor) -> git add . -> fortsätt/kör om pop om behövs.

Behöver bara en fil? git checkout stash@{0} -- path/to/file

---

---

Snabb “lathund” att visa

- Cherry-pick: log → switch main → cherry-pick <SHA> → (ev. lös) → --continue

- Stash: stash push -m → switch → fix → switch - → stash list/show → pop/apply

- Konflikt: skapa → lös i editor → add → commit → kör test

- Rebase -i: städa lokalt före push (reword/squash) → --continue/--abort

- Ångra rätt: reset (före push) | revert (efter push)

---

---

🧠 Övningar från slide 89 och 91 samt så finns också fler i exercises mappen
