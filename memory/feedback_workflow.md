---
name: Kaldea HTML workflow
description: Regler for hvordan man arbejder med Kaldea hjemmeside HTML-filen
type: feedback
---

Brug altid Python-scripts til at ændre HTML-filen. Aldrig direkte redigering med Edit-tool.

**Why:** Filen er ~2.8 MB med base64-embedded billeder. Read tool og Edit tool fejler eller misser indhold på filer af den størrelse.

**How to apply:**
1. Skriv et Python-script til C:\Users\niels\Desktop\kaldea-website\
2. Kør det med: `cd "C:\Users\niels\Desktop\kaldea-website" ; python scriptname.py`
3. Slet scriptet bagefter
4. Synkroniser til subfolder: `Copy-Item "index hjemmeside.html" "kaldea-website\index hjemmeside.html"`
5. Commit og push

Brug altid `sys.stdout.reconfigure(encoding='utf-8')` øverst i scripts.
Brug eksplicitte string-matches (ikke regex) til CSS-replacements.
