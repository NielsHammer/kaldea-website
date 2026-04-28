# Kaldea — Project Briefing

## Hvad er Kaldea?

Kaldea er et dansk B2B-kaffeselskab der leverer kaffemaskiner, vandautomater og vending-maskiner til arbejdspladser — typisk på abonnement med tilhørende kaffe- og serviceaftaler (MRR-model).

Hjemmeside: kaldea.dk (hosted på Simply.com, manuelt FTP-upload)
CRM (under opbygning): crm.kaldea.dk (Vercel)

GitHub: https://github.com/NielsHammer/kaldea-website

---

## Teamet

| Navn | Rolle |
|------|-------|
| Markus | Admin |
| Jonas | Admin |
| Mathias | Admin |
| Brian | Admin |
| Niels | Admin (primær udvikler på dette projekt) |

CRM-roller der bygges: **admin**, **sælger**, **chauffør**

---

## Produktkatalog

### Kaffemaskiner
- **Rhea rhTT1.v+** — hele bønner
- **Wittenborg W100 R&G** — malet kaffe
- **Rhea rhTT1.i** — instant

### Vandautomater
- **rH2O.20**
- **rH2O.60**
- **Cool Aqua Plus**
- **Cool Mix** (2 produktbilleder)

### Vending
- **Luce Zero Side Snack**
- **Luce XL6 Multishop**
- **Saphirh Shop Pro**

---

## Projektstruktur

```
kaldea-website/          ← git-repo (GitHub)
  index hjemmeside.html  ← marketing website (enkelt HTML-fil, ~1.2 MB, inline CSS+JS)
  index CRM.html         ← gammel CRM prototype (enkelt HTML-fil, localStorage, erstattes)

memory/                  ← Claude Code-hukommelse (ikke del af git-repo)
CLAUDE.md                ← denne fil
```

Der findes desuden projektfiler (ikke i repo endnu) med:
- **Priser** — maskinpriser og abonnementspriser
- **Kunder** — eksisterende kundeliste
- **Leads** — aktiv salgspipeline
- **Maskindokumentation** — tekniske specifikationer og manualer

Disse skal importeres til den nye Supabase-database når CRM bygges.

---

## Plan

### Hjemmeside (`index hjemmeside.html`)
Enkelt HTML-fil. Ændringer laves direkte i filen og uploades manuelt til Simply.com.

**Ventende ændringer:**
1. Navigation i rigtig rækkefølge ift. sektioner på siden
2. Forenklet kontaktformular — ingen maskinvalg
3. Udskift brandnavn "Necta" med "Animo"
4. Fjern alle EM dashes (—) i tekst
5. Kaffe-animation kun i hero-sektionen, ikke andre steder

### CRM (nyt projekt fra bunden)
Erstatter `index CRM.html`-prototypen med en proper app.

**Tech stack:**
- **Database:** Supabase (PostgreSQL + real-time subscriptions)
- **Frontend:** Next.js (App Router)
- **Hosting:** Vercel → crm.kaldea.dk
- **Auth:** Supabase Auth med rollebaseret adgang

**CRM-moduler der bygges:**
- Dashboard (KPI: kunder, MRR, leads, leveringer, opgaver)
- Pipeline/Leads (Kanban: Kontaktet → Møde → Tilbud → Vundet/Tabt)
- Kunder (kundekort med kontrakt, maskine, leveringsfrekvens, MRR)
- Leveringer (planlægning og chauffør-visning)
- Kalender (leveringsoverblik)
- Lager (produktbeholdning med genbestillingsniveau)
- Opgaver (team to-dos med prioritet og ansvarlig)

---

## Design-DNA (hjemmeside)

- **Farver:** Mørk brun `#0e0600`, guld `#c47a2b` / `#e8a444`, cream `#f5ede0`
- **Fonte:** Cormorant Garamond (serif, headlines) + DM Sans (sans, brødtekst)
- **Tone:** Premium, dansk, B2B — ikke hipster-kaffe, men professionel arbejdspladsløsning
- **Animationer:** Partikler-canvas i baggrund, SVG kaffekop-animation (kun i hero)

## Design-DNA (CRM)

- Samme farvepalette, lys baggrund (`#f7f3ee`)
- Kompakt, informationstæt UI — ikke et consumer-produkt
- Cormorant Garamond til overskrifter, DM Sans til data

---

## Vigtige detaljer

- Hjemmesidens HTML-fil er meget stor (~1.2 MB) — brug `offset`/`limit` ved læsning
- CRM-prototypen gemmer data i `localStorage` — ingen backend endnu
- Simply.com understøtter ikke server-side kode — hjemmesiden forbliver statisk HTML
- Alle tekstændringer på hjemmesiden skal holde dansk tone og undgå EM dashes
