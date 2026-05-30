---
name: Kaldea project overview
description: Context, plan, and product details for the Kaldea Kaffe project
type: project
---

Kaldea er et dansk B2B-kaffeselskab der leverer kaffemaskiner, vandautomater og vending til arbejdspladser.

Repo: https://github.com/NielsHammer/kaldea-website
Git root: C:\Users\niels\Desktop\kaldea-website\
HTML-filer tracket direkte i git-roden (ikke i undermapper).
Der findes OGSÅ en kopi i undermappen kaldea-website/ — hold dem synkroniseret med Copy-Item efter ændringer.

---

## PLAN

- **Hjemmeside** (`index hjemmeside.html`): standalone HTML, hostet på Simply.com (manuel FTP-upload)
- **CRM**: rebuildes fra bunden — Supabase + Next.js + Vercel (crm.kaldea.dk)

---

## PRODUKTER

**Kaffemaskiner:**
- Rhea rhTT1.v+ (hele bønner) — rhea-rhTT1v-hele-boenner.png
- Wittenborg W100 R&G (malet kaffe) — wittenborg-W100-malet-kaffe.png
- Rhea rhTT1.i (instant) — rhea-rhTT1i-instant.png

**Vandautomater:**
- Rhea rH2O.20 — rhea-rH2O20.png
- Rhea rH2O.60 — rhea-rH2O60.png
- Rhea Cool Aqua Plus — rhea-cool-aqua-plus.png
- Rhea Cool Mix — rhea-cool-mix-kaffe-look.png + rhea-cool-mix-smoothie-look.png

**Vending:**
- Rhea Luce Zero Side Snack — rhea-luce-zero-side-snack.png
- Rhea Luce XL6 Multishop — rhea-luce-xl6-multishop.png
- Rhea Saphirh Shop Pro — rhea-saphirh-shop-pro.png

Alle PNG-filer: transparente baggrunde (behandlet med fal.ai rembg). Embedded som base64 i HTML.

---

## HJEMMESIDE STATUS (seneste commit: 8cebbb8, 2026-04-29)

Filen er 2.84 MB. Brug altid Python-scripts til ændringer — aldrig direkte redigering.

### Hvad er på plads:

1. **Navigation:** Logo PNG (height:55px, base64 embedded, transparent), rækkefølge: Maskiner → Konceptet → Gratis tilbud → Om os → Kontakt
2. **Hero:** Mørk baggrund med SVG kaffekop animation og partikler
3. **Tbar:** Hurtig service garanti / Leveringsmuligheder / Service inkluderet / Telefon
4. **Maskine-sektion:** Mørk animeret baggrund (gradShift), tab-navigation (Kaffemaskiner / Vandautomater / Vending), 11 maskiner med base64-billeder, stage light/glow, premium hover
   - Cool Mix: thumbnail-skifte mellem kaffe-look og smoothie-look
5. **Brand bar:** RHEA / WITTENBORG / BRAVILOR / ANIMO — guld linjer over/under, lysere farver
6. **Koncept-sektion:** 4 kort med guld-numre (01–04), mørk baggrund, guldkant
   - Kort 01: De rigtige maskiner
   - Kort 02: Kaffe til jeres smag
   - Kort 03: Levering der passer jer
   - Kort 04: Hurtig hjælp når det gælder
7. **Gratis tilbud sektion:** Mørk, formular med Formspree
8. **Services sektion:** Alt hvad I har brug for
9. **Hvorfor Kaldea sektion:** 4 punkter
10. **Om os sektion:** Unsplash foto, tekst om virksomheden
11. **Kontakt sektion:** Formular + detaljer
12. **Footer**

### Hvad er fjernet (må IKKE genindføres):
- scwrap/scstick: "Én løsning. Al kaffen ordnet." — fjernet med vilje
- Kaffekop SVG illustration der lå løst efter tbar — fjernet
- Alle em dashes (—) og en dashes (–) — erstattet med komma/kolon

### CSS-variabler:
- --gold:#c47a2b, --goldlt:#e8a444, --dark:#0e0600, --cream:#f5ede0
- Fonte: Cormorant Garamond (serif, --serif), DM Sans (sans, --sans)
- Nøgle-animation: gradShift (bruges på maskine-sektion baggrund)

---

## VIGTIGE DETALJER

- HTML-filen er ~2.84 MB — brug altid Python-scripts (Read tool fejler på store filer)
- Brug altid Python-scripts til større HTML-ændringer (skriv til fil, kør, slet)
- Simply.com: manuel FTP-upload af index hjemmeside.html + alle PNG-filer
- Alle maskinebilleder er embedded som base64 i HTML → siden er self-contained
- Logo er embedded som base64 PNG (~430KB) i nav
- Synkroniser altid: Copy-Item "index hjemmeside.html" "kaldea-website\index hjemmeside.html"

---

## CRM TECH STACK

- Database: Supabase (PostgreSQL + real-time)
- Frontend: Next.js (App Router)
- Hosting: Vercel → crm.kaldea.dk
- Auth: Supabase Auth med roller: admin, sælger, chauffør
- Team: Markus, Jonas, Mathias, Brian, Niels (alle admins)
