# Övning 1 – Skapa och lös merge-konflikter

**Syfte:** Träna på att skapa, förstå och lösa konflikter i Git (manuellt och via VS Code Merge UI).  
**Arbetssätt:** Parvis (A och B) i samma repo (t.ex. ett privat repo per par).

## Förbered

1. Synka main:
   git switch main
   git pull

Skapa varsin feature-branch:

Person A:

git switch -c feat/a-style

Person B:

git switch -c feat/b-style

Skapa konflikt

Båda ändrar samma rad i samma fil (t.ex. src/styles.css):

Person A sätter:

.box { width: 300px; }

Person B sätter:

.box { width: 15em; }

Båda committar:

git add .
git commit -m "Style: adjust .box width"

Mergea till main i tur och ordning:

Person A:

git switch main
git merge feat/a-style
git push

Person B:

git switch main
git merge feat/b-style # <- konflikt uppstår

Lös konflikten

Öppna filen i VS Code. Du ser markörer:

<<<<<<< HEAD
.box { width: 300px; }
=======
.box { width: 15em; }

> > > > > > > feat/b-style

Välj Accept Current eller Accept Incoming (eller kombinera manuellt t.ex. använda clamp() om ni vill).

Avsluta merge:

git add src/styles.css
git commit -m "Resolve merge conflict (.box width)"
git push

Kontroll & reflektion

Kolla historiken:

git log --graph --oneline --decorate --all

Frågor:

Vad triggar en konflikt?

Vad betyder HEAD i konfliktmarkörerna?

När är “Accept Both” rimligt?

Klart när

Konflikten är löst, main är pushad och historiken visar merge-commit.

---
