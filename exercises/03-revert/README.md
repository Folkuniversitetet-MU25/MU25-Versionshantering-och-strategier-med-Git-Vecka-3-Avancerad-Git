# 03 – Revert: ångra säkert i delad historik

**Mål:** Använd `git revert` (inte `reset`) för att backa i delad historik utan att förstöra commit-kedjan.

> **Arbeta i ditt eget repo.** PR öppnas i ditt repo.

## Förbered
- På `main`: lägg en “felaktig” commit (t.ex. `feat: experimental bg color` i en css/txt-fil).

## Uppgift
1. `git revert <SHA>`
2. Push och öppna PR. Svara kort på:
   - Varför är **revert** säkrare än `reset` i delade repos?
   - När hade `reset` varit OK?

## Godkänt när
- [ ] Ny “revert”-commit finns i historiken
- [ ] PR motiverar valet (review av klasskamrat är frivillig)
