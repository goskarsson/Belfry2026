# Belfry 2026 — Lifandi mælaborð

Read-only útgáfa af Belfry 2026 mælaborðinu, ætluð til að hýsa á GitHub Pages og deila með leikmönnum.

## Skrár

- `index.html` — Mælaborðið sjálft (eitt sjálfstætt skjal, engar ytri kröfur)
- `README.md` — Þessi skrá

## Hvað sýnir mælaborðið?

**Efst:**
- Belfry-þema haus með kvöldhimni, hæðum, klúbbhús-skuggamynd, vatnshættu og fána
- Ryder Cup banner — stór skor-tölur (Hafnarfjörður vs Restin)

**Tölfræði-spjöld** (síanleg eftir degi með Sía-tökkum: Allir dagar / D1 / D2 / D3 / D4 / D5):
- 🏆 **Belfry 2026 meistarinn** — 3 bestu hringir (Top 3 punkta)
- 📈 **Hreyfingar dagsins** — 5 sem bættu sig mest og 5 sem versnuðu mest milli daga
- 🍻 **Drykkurinn** — inneign og skuld eftir D1+D2 holukeppnir, hover yfir nafn sýnir hverja viðkomandi spilaði gegn og drykkjaflæði
- 🏠 **Besta herbergið** — samanlagðir punktar herbergisins (sýnir leikmenn í nafninu, t.d. H9 Guðmundur-Gísli)
- ⛳ **Besti kylfingurinn** — lægstu samanlögðu högg
- 🐦 **Fuglasöngvarinn** — flestir fuglar
- 🎯 **Næstur holu** — minnsta cm-mæling á par 3
- 🏌️ **Holumeistarinn** — oftast næst holu

**Röðun-örvar (▲▼)** birtast á 4 fyrri spjöldum og fylgja síunni:
- Allir dagar: ber saman D-latest við D-latest-1 (cumulative)
- Tiltekinn dagur: ber saman þann dag við daginn á undan
- Smelltu "Sýna alla" til að sjá alla leikmenn

**Spilara-tafla** með:
- Forgjöf (handicap index, fastur fyrir hvern leikmann, t.d. 10,4)
- Leikforgjöf (course handicap per dag — breytileg milli valla)
- Högg, Punktar, Fuglar — fyrir valda daginn
- Cumulative dálkar: Top 3 pts, Σ pts, Σ högg, Σ fuglar
- CTP mælingar, Næst (cm), Holu#
- 🍻 — Drykkjastaða leikmanns (±N)
- Smelltu á dálkfyrirsögn til að raða

**Drykkurinn matchsheet** (samanbrotanlegt, neðst):
- D1 (1 drykkur í veði) og D2 (2 drykkir í veði) hvor með 16 pörum
- Sigurvegari grænn, tapari grár með strok-yfir
- Örvar sýna í hvora áttina drykkir flæða

## Uppsetning á GitHub Pages (eitt sinn, ~10 mín)

### 1. Búa til GitHub repo

1. Farðu á https://github.com/new
2. Repository name: `Belfry2026` (eða eitthvað sem þú vilt)
3. Visibility: **Public**
4. Hakaðu **við** "Add a README file"
5. Smelltu "Create repository"

### 2. Hlaða upp skjölunum

1. Smelltu á "Add file" → "Upload files"
2. Dragðu `index.html` og `README.md` úr þessari möppu inn
3. Skrunaðu niður og smelltu "Commit changes"

### 3. Kveikja á GitHub Pages

1. Settings → Pages
2. Source: "Deploy from a branch", branch `main`, folder `/ (root)`
3. Save
4. Bíddu 1-2 mín

### 4. Hlekkurinn

Birtist efst á Pages síðunni, t.d. `https://goskarsson.github.io/Belfry2026/`

## Dagleg uppfærsla (eftir hvern hring)

1. Þú slærð inn skor í Cowork-mælaborðinu (eða ég les úr skjáskotum)
2. Þú segir mér: **"byggðu snapshot fyrir GitHub"**
3. Ég bý til nýtt `index.html` með núverandi stöðu innbökuðu
4. Þú ferð á GitHub.com → repo-ið → smellir á `index.html` → "Edit" táknið
5. Eyðir öllu innihaldi og límir nýja útgáfu
6. "Commit changes"
7. ~30-60 sek seinna er síðan uppfærð

**Mun auðveldara verkflæði** með GitHub Desktop (sækja frá https://desktop.github.com):
1. Klóna repo-ið á tölvuna
2. Þegar ég uppfæri `index.html` skjalið → GitHub Desktop sér breytinguna → Commit + Push með einum smell

## Tækni-glósur

- **Sjálfstætt skjal** — engar ytri CDN-tilvitnanir, eitt HTML skjal
- **Mobile-friendly** — virkar á símum
- **localStorage** — geymir bara persónulegar UI stillingar viewersins (valinn dagur, sía, "Sýna alla")
- **Snapshot-gögn** eru innbökuð í `<script type="application/json" id="snapshot">` blokk
- Gagnasniðmát:
  ```json
  {
    "lastUpdated": "2026-05-14T20:00:00",
    "ryder": { "hafn": 5, "rest": 3 },
    "players": {
      "8": {
        "strokes": { "s1": 47, "s2": null, "s3": null, "s4": null, "s5": null },
        "points":  { "h1": 12, ... },
        "birdies": { "r1": 1, ... },
        "playingHcp": { "ph1": 11, ... },
        "ctp": [120, 250]
      }
    },
    "drinkMatches": {
      "d1": [ { "p1": 8, "p2": 14, "winner": 1 }, ... ],
      "d2": [ { "p1": 8, "p2": 14, "winner": 2 }, ... ]
    }
  }
  ```
  - `winner`: 1 = p1 vann, 2 = p2 vann, 0 = jafntefli (0 drykkir til hvors)

## Spurningar

Spurningar eða óskir? Bara senda skilaboð í Cowork.
