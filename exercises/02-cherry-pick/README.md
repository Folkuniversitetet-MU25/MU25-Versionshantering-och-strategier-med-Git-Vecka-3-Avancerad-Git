# 02 – Cherry-pick: hotfix mellan grenar

**Mål:** Flytta en specifik fix mellan två grenar utan att mergea allt.

> **Arbeta i ditt eget repo.** PR öppnas i ditt repo.

## Förbered (en gång)
Skapa en release-gren från `main`:
```bash
git checkout main
git checkout -b release/1.0
git push -u origin release/1.0
git checkout main
```

## Uppgift
1. På `main`: gör en liten buggfix och committa (ex: `fix: null-check in login`).
2. Hämta SHA för fix-committen: `git log --oneline`.
3. Byt till `release/1.0` och kör `git cherry-pick <SHA>`.
4. Öppna PR (release/1.0 → main) som förklarar **varför** cherry-pick användes och ev. risker (t.ex. dubbla commits om man cherry-pickar fram och tillbaka).

## Godkänt när
- Fix-committen finns i båda grenarna.
- Din PR beskriver motivet och du har minst **1 review**.
