# Lovable-promptok az oldalaudit alapján

*2026. október 22. · A promptok a Lovable-projekt mostani kódjához készültek (fájlnevek, szövegek, színek).*

---

## Hova és hogyan illeszd be?

1. Nyisd meg a **lovable.dev** oldalon a **Rajmi Investments** projektet (szerkesztő nézet).
2. A bal oldali **chat panel alján** van egy szövegmező („Ask Lovable…”). **Ide** másold be a szürke dobozban lévő szöveget, mindig **egy dobozt egyszerre**, és küldd el (Enter).
3. A szövegmező mellett ne a **„Chat”** (tervezés) mód legyen kiválasztva, hanem az alap (építő) mód. Ha a Lovable mégis tervet mutat, kattints az **„Approve” / „Implement plan”** gombra.
4. Ha **adatbázis-módosítást** kér jóváhagyni (A10-es prompt), hagyd jóvá.
5. Várd meg, amíg végez. Nézd meg a jobb oldali előnézetet az **„Ellenőrzés”** sor alapján, és csak utána küldd a következőt.
6. A **`[[…]]`** jelölésű részeket **küldés előtt írd át** a saját valós adataidra. Ha egy adatod nincs meg, ne küldd el azt a promptot, szólj, és megoldjuk.
7. **Tartsd a sorrendet.** Több prompt ugyanazt a fájlt módosítja, és a későbbiek építenek a korábbiakra.

### Melyik prompt melyik oldalt módosítja?

A Lovable-ben **minden promptot ugyanoda illesztesz be: a bal oldali chat mezőbe.** Nincs oldalankénti külön beillesztési hely, a prompt maga írja meg a Lovable-nek, melyik fájlt módosítsa. Érdemes viszont küldés előtt az előnézetben **arra az oldalra navigálni**, amelyiket a prompt módosítja (az előnézet feletti címsorban, pl. `/booking`). Így a változást utána azonnal látod.

| Prompt | Melyik oldal | Melyik rész | Előnézet címe |
|---|---|---|---|
| A1 | **Minden oldal** | Lábléc → „Kapcsolat” oszlop (e-mail, LinkedIn) | `/` (bármelyik oldal alja) |
| A2 | **Főoldal** | A hero jobb oldali „Eredmények összegzése” doboza | `/` |
| A3 | **Új oldal: Eredmények** + menü és lábléc | Teljes trade-napló; új „Eredmények” menüpont | `/eredmenyek` |
| A4 | **Főoldal** | A hero alatti trade-kártyák (most „Valós eredmények”) és a piros „Figyelmeztetés” sáv | `/` |
| A5 | **Főoldal** | Kikerül: „Aggódsz…?”, „Mielőtt tovább görgetsz”, kalkulátor | `/` |
| A6 | **Főoldal** + **Foglalás** | Önteszt („Hol tartasz most?”) eredménye; a foglalási űrlap üzenetmezője | `/`, majd `/booking` |
| A7 | **Új oldal: Impresszum** + lábléc | Impresszum; jogi linkek a lábléc legalján | `/impresszum` |
| A8 | **Új oldal: Adatkezelési tájékoztató** | – | `/adatkezeles` |
| A9 | **Új oldal: ÁSZF** | – | `/aszf` |
| A10 | **Foglalás** | Naptár, időpontok, jelölőnégyzet a gomb felett (+ háttér: adatbázis) | `/booking` |
| A11 | **Segítség** | Gyakori kérdések válaszai, „Probléma bejelentése” rész | `/segitseg` |
| A12 | **Rólam** | Fotó melletti üres részek, „Az utam” alcíme, statisztikasáv | `/about` |
| A13 | **Minden oldal** | Piros „1” jelzés a jobb alsó chat ikonon | `/` |
| B1 | **Főoldal** | Új rész közvetlenül a hero (főcím) alatt | `/` |
| B2 | **Főoldal** + **Folyamat** | Új rész az infláció és az önteszt között; a Folyamat oldalon a 3. lépés neve | `/`, majd `/process` |
| B3 | **Főoldal** | Új rész a legvégén, a lábléc előtt | `/` |
| C1 | **Foglalás** | Az egész oldal színei, betűi | `/booking` |
| C2 | **GYIK** | Az egész oldal színei, betűi | `/faq` |
| C3 | **Főoldal** + **Rólam** | Főoldal: „Beszéljünk a pénzügyi céljaidról” doboz és az inflációs gomb; Rólam: „Az utam” kártyái | `/`, majd `/about` |
| C4 | **Főoldal** | Inflációs blokk („Befektetés nélkül a pénzed nem pihen.”) | `/` |

Oldalanként csoportosítva:
- **Főoldal (`/`):** A2, A4, A5, A6, B1, B2, B3, C3, C4
- **Rólam (`/about`):** A12, C3
- **Folyamat (`/process`):** B2 (csak a 3. lépés neve)
- **Foglalás (`/booking`):** A6 (előkitöltés), A10, C1
- **GYIK (`/faq`):** C2
- **Segítség (`/segitseg`):** A11
- **Új oldalak:** A3 (`/eredmenyek`), A7 (`/impresszum`), A8 (`/adatkezeles`), A9 (`/aszf`)
- **Minden oldal (lábléc, menü, chat ikon):** A1, A3, A7, A13

| Jel | Jelentés |
|---|---|
| 🔴 **A** | Publikálás előtt kötelező (P0) |
| 🟡 **B** | A meggyőzőerőhöz (P1) |
| ⚪ **C** | Csiszolás (P2) |

---

# 🔴 A – Kötelező javítások

## A1 · Elérhetőségek egy helyen + e-mail-cím javítása

> **Előtte töltsd ki:** a helyes e-mail-címed és a LinkedIn-profilod linkje. Ha nincs LinkedIn, hagyd üresen az idézőjelek között.

```
CONTEXT: The footer (src/components/site/Footer.tsx) hardcodes the contact email as "info@rajminvestments.com", which is probably a typo of the brand name "Rajmi Investments". LINKEDIN_URL is an empty string. Several upcoming changes need the same contact data, so it should live in one place.

ACTION:
1. Create src/lib/contact.ts exporting two constants:
   export const CONTACT_EMAIL = "[[helyes-email@domain.hu]]";
   export const LINKEDIN_URL = "[[https://www.linkedin.com/in/... vagy üres]]";
2. In Footer.tsx remove the local LINKEDIN_URL constant and import both constants from "@/lib/contact". Use CONTACT_EMAIL for both the mailto: href and the visible text. Keep the existing behaviour that the LinkedIn link is only rendered when LINKEDIN_URL is not empty.
3. Search the whole project (src/ and supabase/functions/) for "rajminvestments" and "info@" and replace every hardcoded contact email with CONTACT_EMAIL (in frontend code) or the same string value (in edge functions / email templates). List in your reply every file you changed.

RESULT: One source of truth for the contact email and LinkedIn URL, with the typo fixed everywhere.
```
**Ellenőrzés:** a lábléc „Kapcsolat” oszlopában a helyes e-mail-cím látszik, és rákattintva a leveleződ azt a címet nyitja meg.

---

## A2 · Őszinte statisztika – a dátum nélküli trade-ek külön

> **Miért?** A naplóban 8 dátum nélküli, mind nyereséges BTC/MSTR tétel van, és ezek felhúzzák a statisztikát. **Velük:** 101 trade · 55% · +3,40%. **Nélkülük:** 93 trade · 52% · +1,88%. Ellenőrizhetetlen adatot egy pénzügyi oldalon nem szabad a fő számokba beszámítani. Ha később megadod a dátumaikat, visszakerülhetnek.

```
CONTEXT: src/components/site/TradeResults.tsx exports `trades`, which contains 93 dated trades and 8 undated BTC/MSTR trades (date: null, position: null, all profitable, all with the same 60000 entry). These undated, unverifiable trades are included in every statistic: the hero summary box in HeroTerminal.tsx (101 / 55% / +3,40%) and the summary strip in TradeResults. For an honest public trade log, statistics must only use verifiable (dated) trades.

ACTION:
1. In TradeResults.tsx add and export:
   export const datedTrades = trades.filter((t) => t.date !== null);
   export const undatedTrades = trades.filter((t) => t.date === null);
2. In HeroTerminal.tsx compute ALL hero stats (count, win rate, average return per trade, latest date) from `datedTrades` instead of `trades`.
3. In TradeResults.tsx compute the summary strip (Lezárt trade, Sikeres pozíció, Átlagos hozam / trade) from `datedTrades`. Show negative average in red (text-red-400) instead of always emerald.
4. In the TradeResults card grid, render only datedTrades. Below the grid, add a separate, collapsed-by-default block (use a simple button toggle) titled "Dátum nélküli korábbi trade-ek (nem számítanak bele a statisztikába)" that lists undatedTrades with the same card component, at 70% opacity, with the date shown as "dátum nélkül".
5. Do not change any trade values.

RESULT: All public statistics are based only on the 93 dated trades (currently 93 / 52% / +1,88%); the 8 undated trades remain visible but clearly separated and excluded.
```
**Ellenőrzés:** a főoldali eredménydoboz **93 / 52% / +1,88%** értéket mutat.

---

## A3 · Új oldal: a teljes trade-napló (`/eredmenyek`)

```
CONTEXT: The site promises a "Nyilvános trade-napló – a veszteségekkel együtt" (public trade log including losses), but the full list is not reachable anywhere: the TradeResults component (src/components/site/TradeResults.tsx) already renders the complete log with filters, but no page uses it.

ACTION:
1. Create src/pages/ResultsPage.tsx that renders <Layout> with a top padding wrapper (pt-32, same as AboutPage) and the existing <TradeResults /> component.
2. Register the route "/eredmenyek" in src/App.tsx above the catch-all route.
3. In TradeResults.tsx:
   a) Change the subtitle area under the H2 "Valós trade-jeim, átláthatóan": add one muted mono paragraph (14px, max-w-2xl, centered): "Minden lezárt ügyletem, nyereség és veszteség egyaránt. A hozam az adott ügylet belépő és kilépő árából számolt százalék, pozícióméret nélkül – nem a teljes tőkém változása."
   b) Set the default date sort to "newest" (already) and make sure the default yield sort is "none" so losses are not hidden at the bottom.
   c) Replace the large red warning box at the bottom (border-2 border-red-500/50 … text-lg md:text-xl font-extrabold text-red-600) with a calm, small line: centered, term-mono, 12px, color var(--term-text-muted), max-w-3xl: "A múltbeli teljesítmény nem garancia a jövőbeli eredményekre. Ez a napló tájékoztató jellegű, nem minősül befektetési tanácsadásnak."
4. Add "Eredmények" (to "/eredmenyek") to the navbar links (src/components/site/Navbar.tsx) right after "Rólam", and to navLinks in Footer.tsx in the same position.

RESULT: A dedicated page with the complete, honest trade log, linked from the navigation.
```
**Ellenőrzés:** a menüben megjelenik az „Eredmények” pont. Az oldalon a legújabb trade-ek vannak elöl, a veszteségek pirossal.

---

## A4 · A főoldali trade-blokk: a legutóbbi 8 trade, veszteségekkel együtt

```
CONTEXT: On the homepage, src/components/site/Hero.tsx contains a hardcoded `bestTrades` array with only 8 winning trades, a "Legjobb hozam" default sort and date filters ("Utolsó 30/90 nap") that currently return an empty list. This contradicts the hero promise "Nyilvános trade-napló – a veszteségekkel együtt". Above it there is a loud red "⚠ Figyelmeztetés" strip that is the first thing visitors see after the hero.

ACTION:
1. In Hero.tsx delete the `bestTrades` array. Import `datedTrades` and `computeReturn` from "@/components/site/TradeResults". The showcase shows the 8 most recent dated trades (sorted by date, newest first), regardless of result.
2. In TradeShowcase remove the date-range select, the sort select and the Long/Short buttons (they are not needed for 8 items). Keep the card design, the sequential reveal and TiltCard.
3. Each card must reflect the real result: positive → green (var(--term-accent-green)) with TrendingUp and a "+" sign; negative → red (var(--term-accent-red)) with TrendingDown and the minus sign (no extra "+"). Use computeReturn for the value. Make the small arrow between entry and exit price neutral (var(--term-text-muted)) instead of always green.
4. Header of the block:
   - Title (replace "Valós eredmények"): "Legutóbbi trade-jeim – a veszteségekkel együtt"
   - Under it a one-line mono summary computed from datedTrades: "{N} lezárt trade · {winRate}% nyerési arány · {avg}% átlag / trade" (Hungarian number format, one decimal for avg, sign included).
   - Right side (where the filters were): a link to "/eredmenyek" with text "Teljes trade-napló →" in var(--term-accent-blue), term-mono 13px.
5. Delete the red "DISCLAIMER STRIP" section and the 40px spacer below it. Instead, directly under the card grid add one small centered line: term-mono, 12px, var(--term-text-muted): "A múltbeli teljesítmény nem garancia a jövőbeli eredményekre. Nem minősül befektetési tanácsadásnak."
6. In src/components/site/HeroTerminal.tsx change the footer link of the results box from "TOP TRADE-EK MEGTEKINTÉSE →" (href "#eredmenyek") to "TELJES TRADE-NAPLÓ →" linking to "/eredmenyek" (react-router Link).
7. Keep the id="eredmenyek" on the showcase wrapper.

RESULT: The homepage shows real, recent trades including losses, and links to the full log. The page no longer contradicts its own promise.
```
**Ellenőrzés:** a főoldalon a hero alatt 8 kártya van, köztük pirosak is (CRWV −16,62%, ETH −8,82%, VIRTUAL −1,37%). A piros figyelmeztető sáv eltűnt.

---

## A5 · A főoldal karcsúsítása (3 szekció ki)

> **Mit vesz ki:** az „Aggódsz…?” oszlopdiagramot (számok és forrás nélkül), a „Mielőtt tovább görgetsz” piros blokkot (bizonytalan forrásokkal) és a kalkulátort (irreális hozamok, személyre szabott portfólió – jogi kockázat). A fájlok megmaradnak, csak a főoldalról kerülnek le, így bármikor visszahozhatók.

```
CONTEXT: The homepage (src/pages/Index.tsx) is too long and contains three problematic sections:
- SavingsHook: a fear chart with no numbers, time frame or source, and a button "görgess lejjebb a megoldásért!" that leads to more fear content, not a solution.
- ShockDataSection: statistics attributed to "ESMA, 2024" and "ESMA leverage study" that cannot be verified, and the content is about leveraged traders, not beginner savers.
- InvestmentCalculator: shows unrealistic returns (the "pessimistic" growth scenario is still +11%/year with 20% crypto) and a "személyre szabott portfólió" with concrete allocations, which could be considered personalised investment advice (licence required in Hungary).

ACTION:
1. In src/pages/Index.tsx remove <SavingsHook />, <ShockDataSection /> and <InvestmentCalculator /> together with their wrapper divs and SequencedSection wrappers, and remove the unused imports. Do NOT delete the component files.
2. Renumber the remaining SequencedSection `index` props so they are consecutive starting at 1 in their order on the page (the sequence system only unlocks a section after index-1 has completed, so gaps would hide sections).
3. Keep alternating background bands (term-band-alt / term-band) alternating correctly after the removal.
4. If src/test/shock-conclusion-gate.test.tsx imports ShockDataSection, keep it working (the component file still exists).

RESULT: Homepage order: HeroTerminal → recent trades + CTA (Hero) → inflation (InflationRealValue) → self-test (FinancialQuiz). Nothing hidden, no gaps in the sequence.
```
**Ellenőrzés:** a főoldalt lassan végig kell görgetni, és minden szekciónak meg kell jelennie (nincs üres, láthatatlan rész). Az önteszt után jön a lábléc.

---

## A6 · Az önteszt eredménye után következő lépés

```
CONTEXT: In src/components/site/FinancialQuiz.tsx the result card (shown when all 8 questions are answered) has a title and description but no next step. The visitor reaches a dead end.

ACTION:
1. Inside the result card, under the description, add a primary CTA button linking to "/booking" (react-router Link): "Beszéljük át az eredményed – ingyenes 30 perces konzultáció →". Use the same visual style as the hero primary button (className "hero-terminal-primary term-mono" via the shadcn Button asChild pattern used in HeroTerminal.tsx).
2. Under the button add a small muted line (term-mono, 12px): "30 perc · online · kötelezettség nélkül".
3. When the result card appears, smoothly scroll it into view (scrollIntoView({ behavior: "smooth", block: "center" })), respecting prefers-reduced-motion (instant scroll when reduced).
4. Pass the result to the booking page: link to `/booking?onteszt=${encodeURIComponent(result.title)}`. In src/pages/BookingPage.tsx read the "onteszt" query param and, if present, prefill the "Miben segíthetek?" textarea with: "Önteszt eredményem: {title} ({total}/32 pont)." (also pass total as a "pont" param).

RESULT: The self-test leads directly to a booking, with the result carried over.
```
**Ellenőrzés:** az önteszt kitöltése után megjelenik a gomb, és a foglalási oldalon az üzenet mezőben már ott az eredmény.

---

## A7 · Impresszum + jogi linkek a láblécben

> **Előtte töltsd ki** az összes `[[…]]` mezőt. Ezek törvény szerint kötelező adatok (Ekertv. 4. §). A tárhelyszolgáltató adatait a Lovable jogi oldalán találod (lovable.dev → Legal / Terms). **Élesítés előtt mutasd meg jogásznak vagy könyvelőnek.**

```
CONTEXT: The site collects personal data (booking form, support chat) but has no legal notice (Impresszum), privacy policy or terms. Hungarian law requires an Impresszum. This prompt creates the Impresszum page and the legal link row in the footer; the privacy policy and terms pages come in the next prompts.

ACTION:
1. Create src/pages/LegalPage.tsx: a reusable layout for long legal text. <Layout>, container max-w-3xl, pt-32 pb-24. H1 in Playfair Display 800 (fontFamily var(--font-display), clamp(32px,4vw,48px)), an "Utolsó frissítés: {date}" line (term-mono, 12px, muted), then the content: H2s 22px Playfair 800 with 40px top margin, paragraphs 16px Inter line-height 1.75 color var(--term-text-muted), lists with the same style. Props: title, updated, children.
2. Create src/pages/ImpresszumPage.tsx using LegalPage, route "/impresszum", with exactly this content (Hungarian):

   H1: Impresszum
   Utolsó frissítés: 2026. [[hónap nap]].

   H2: Üzemeltető
   - Név: [[Kovács Rajmond egyéni vállalkozó / cégnév]]
   - Székhely: [[irányítószám, település, utca, házszám]]
   - Nyilvántartási szám: [[EV nyilvántartási szám / cégjegyzékszám]]
   - Adószám: [[adószám]]
   - E-mail: {CONTACT_EMAIL from "@/lib/contact"}

   H2: Tárhelyszolgáltató
   - Név: [[tárhelyszolgáltató neve]]
   - Cím: [[tárhelyszolgáltató címe]]
   - E-mail / weboldal: [[elérhetőség]]

   H2: Fontos tudnivaló
   A weboldal tartalma kizárólag tájékoztató és oktatási célú. Nem minősül befektetési tanácsadásnak, ajánlattételnek vagy befektetésre való felhívásnak. A Rajmi Investments nem rendelkezik a befektetési szolgáltatási tevékenységről szóló törvény (Bszt.) szerinti engedéllyel, ezért személyre szóló befektetési ajánlást nem ad. A befektetés kockázattal jár, a befektetett tőke részben vagy egészben elveszhet. A múltbeli teljesítmény nem garancia a jövőbeli eredményekre.

3. Register "/impresszum" in App.tsx (above the catch-all).
4. In Footer.tsx, in the bottom row (next to the © line), add a legal link row (term-mono, 11px, muted, hover → foreground, separated by " · "): "Impresszum" (/impresszum) · "Adatkezelési tájékoztató" (/adatkezeles) · "ÁSZF" (/aszf). The last two routes will be created by the next prompts; until then they may show the 404 page.

RESULT: A legally required Impresszum page and permanent legal links in the footer.
```
**Ellenőrzés:** a lábléc alján három link van, és az „Impresszum” a kitöltött adatokkal nyílik meg.

---

## A8 · Adatkezelési tájékoztató

> **Előtte töltsd ki** a `[[…]]` mezőket. Ez **sablon**, a pontos megőrzési időket és a szolgáltatók listáját **jogásszal ellenőriztesd**. Az adatfeldolgozókat a valóság szerint írd be: aki tárolja vagy továbbítja az adatot (Lovable/Supabase, e-mail-küldő, Voiceflow, AI-szolgáltató).

```
CONTEXT: The site processes personal data: the booking form (name, email, experience level, message, chosen date/time), the support chatbot on /segitseg (chat messages), transactional emails (email address, send log) and the Voiceflow chat widget on other pages. A privacy policy (GDPR art. 13) is required. Use the LegalPage layout created in the previous prompt.

ACTION:
1. Create src/pages/PrivacyPage.tsx with LegalPage, route "/adatkezeles", content (Hungarian):

   H1: Adatkezelési tájékoztató
   Utolsó frissítés: 2026. [[hónap nap]].

   H2: 1. Az adatkezelő
   [[Név / cégnév]], székhely: [[cím]], e-mail: {CONTACT_EMAIL}. (a továbbiakban: Adatkezelő)

   H2: 2. Milyen adatokat kezelek, miért és meddig?
   Render as a responsive table (on mobile: stacked cards) with columns: Adatkezelés | Adatok | Cél | Jogalap | Megőrzés
   - Időpontfoglalás | név, e-mail-cím, tapasztalati szint, üzenet, választott időpont | a konzultáció egyeztetése és lebonyolítása | GDPR 6. cikk (1) b) – szerződéskötést megelőző lépések | [[a konzultációt követő 1 év]]
   - Ügyfélszolgálati chat (/segitseg) | a chatbe írt üzenetek | kérdések megválaszolása | GDPR 6. cikk (1) f) – jogos érdek | [[30 nap]]
   - Rendszerüzenetek (visszaigazoló e-mail) | e-mail-cím, küldési napló | a foglalás visszaigazolása | GDPR 6. cikk (1) b) | [[1 év]]
   - Csevegőablak (Voiceflow) a többi oldalon | a csevegésbe írt üzenetek | kérdések megválaszolása | GDPR 6. cikk (1) f) – jogos érdek | [[a szolgáltató beállítása szerint]]

   H2: 3. Kik férnek hozzá az adatokhoz? (adatfeldolgozók)
   Az adatokat csak az Adatkezelő ismeri meg. Technikai szolgáltatók (adatfeldolgozók):
   - [[Lovable / Supabase – tárhely és adatbázis, székhely]]
   - [[E-mail-küldő szolgáltató neve]]
   - [[Voiceflow Inc. – csevegőablak]]
   - [[AI-szolgáltató a chatbothoz]]
   Ha valamelyik szolgáltató az Európai Gazdasági Térségen kívül kezeli az adatot, ez az Európai Bizottság általános szerződési feltételei vagy megfelelőségi határozata alapján történik.

   H2: 4. A jogaid
   Kérheted az adataidhoz való hozzáférést, azok helyesbítését, törlését, kezelésük korlátozását, az adathordozhatóságot, és tiltakozhatsz a jogos érdeken alapuló adatkezelés ellen. Kérésedet a {CONTACT_EMAIL} címre küldd, legfeljebb 30 napon belül válaszolok.

   H2: 5. Jogorvoslat
   Panasszal a Nemzeti Adatvédelmi és Információszabadság Hatósághoz (NAIH) fordulhatsz: 1055 Budapest, Falk Miksa utca 9–11., postacím: 1363 Budapest, Pf. 9., www.naih.hu. Bírósághoz is fordulhatsz.

   H2: 6. Sütik
   [[Az oldal csak a működéshez szükséges sütiket / helyi tárolót használja. – vagy a valós lista]]

2. Register "/adatkezeles" in App.tsx above the catch-all.

RESULT: A complete, readable privacy policy page linked from the footer.
```
**Ellenőrzés:** a lábléc „Adatkezelési tájékoztató” linkje működik, és a táblázat telefonon is olvasható.

---

## A9 · ÁSZF

> **Előtte töltsd ki** a `[[…]]` mezőket, különösen az **árat** és a **lemondási szabályt**. Ezt is **jogásszal ellenőriztesd**.

```
CONTEXT: The site offers a free 30-minute consultation and a paid mentoring package (see the offer panel in src/pages/ProcessPage.tsx). General terms (ÁSZF) are needed before taking payments. Use the LegalPage layout.

ACTION:
1. Create src/pages/TermsPage.tsx with LegalPage, route "/aszf", content (Hungarian):

   H1: Általános Szerződési Feltételek
   Utolsó frissítés: 2026. [[hónap nap]].

   H2: 1. A szolgáltató
   [[Név / cégnév]], székhely: [[cím]], adószám: [[adószám]], e-mail: {CONTACT_EMAIL}.

   H2: 2. A szolgáltatás
   Pénzügyi oktatás és mentorálás kezdő befektetőknek, online videóhívásban. A szolgáltatás oktatási jellegű: nem minősül befektetési tanácsadásnak, portfóliókezelésnek vagy személyre szóló befektetési ajánlásnak. A befektetési döntéseidet minden esetben te hozod meg, és te viseled azok kockázatát.

   H2: 3. Ingyenes konzultáció
   Az első 30 perces online konzultáció díjmentes, és semmilyen kötelezettséggel nem jár. Időpontot a weboldal Foglalás oldalán lehet kérni; a foglalást e-mailben igazolom vissza.

   H2: 4. Díjas mentorcsomag
   Ár: [[24 900 Ft]] egyszeri díj ([[alanyi adómentes / bruttó]]). A csomag tartalmát a Folyamat oldal írja le. Fizetés módja: [[átutalás / bankkártya]], a fizetés határideje: [[az első alkalom előtt]].

   H2: 5. Lemondás, módosítás
   Az időpontot legkésőbb [[24 órával]] előtte díjmentesen módosíthatod vagy lemondhatod a {CONTACT_EMAIL} címen. [[Késői lemondás / meg nem jelenés esetén: …]]

   H2: 6. Elállási jog
   Fogyasztóként a szerződéskötéstől számított 14 napon belül indoklás nélkül elállhatsz. Ha kifejezett kérésedre a szolgáltatás teljesítése ezen idő alatt megkezdődik, az addig teljesített rész arányos díját meg kell fizetned; a teljesen teljesített szolgáltatás után elállási jog nem gyakorolható (45/2014. (II. 26.) Korm. rendelet).

   H2: 7. Felelősség
   A mentorálás során elhangzó információk oktatási célúak. A szolgáltató nem felel a felhasználó saját befektetési döntéseiből eredő veszteségekért. A múltbeli teljesítmény nem garancia a jövőbeli eredményekre.

   H2: 8. Panaszkezelés és jogvita
   Panaszodat a {CONTACT_EMAIL} címre küldheted, 30 napon belül válaszolok. Jogvita esetén a lakóhelyed szerint illetékes békéltető testülethez fordulhatsz. A szerződésre a magyar jog az irányadó.

2. Register "/aszf" in App.tsx above the catch-all.

RESULT: General terms page linked from the footer.
```
**Ellenőrzés:** a lábléc mindhárom jogi linkje működik.

---

## A10 · Foglalás: adatkezelési jelölőnégyzet + a foglalt időpontok kizárása

> **Miért?** Most a foglalás **csak e-mailt küld, sehol nem menti el**, ezért ugyanarra az időpontra két ember is foglalhat. A Lovable valószínűleg **adatbázis-módosítást** kér majd jóváhagyni: hagyd jóvá.

```
CONTEXT: src/pages/BookingPage.tsx offers fixed weekday slots (TIME_SLOTS) and calls the edge function supabase/functions/submit-booking, which only sends two emails and does not store anything. So already booked slots stay available (double booking is possible), past times of today are selectable, and there is no privacy notice acknowledgement on the form.

ACTION:
1. Database: create table public.bookings (id uuid pk default gen_random_uuid(), created_at timestamptz default now(), name text not null, email text not null, topic text, slot_date date not null, slot_time text not null, status text not null default 'confirmed'). Add a unique partial index on (slot_date, slot_time) where status = 'confirmed'. Enable RLS with NO public policies (only the service role can read/write).
2. submit-booking: after validation, insert the booking with the service-role client BEFORE sending emails. If the insert fails with a unique violation (Postgres code 23505), return HTTP 409 with { error: "slot_taken" } and send no emails. Also reject dates in the past, weekends and times not in ["09:00","10:00","11:00","13:00","14:00","15:00","16:00","17:00"] with 400.
3. New edge function supabase/functions/booked-slots: GET with query param month=YYYY-MM, returns JSON [{ date: "YYYY-MM-DD", time: "HH:MM" }] of confirmed bookings in that month. Return ONLY date and time, never names or emails. CORS same as submit-booking.
4. BookingPage.tsx:
   a) Fetch booked slots for the visible month (on mount and whenever viewMonth changes). Disable a time slot button when it is booked for the selected date, and show "Foglalt" instead of "30 perc" on it (opacity 40%, cursor-not-allowed).
   b) For today, also disable slots whose time has already passed.
   c) If a day has no free slots left, render it like a non-selectable day.
   d) On 409 from submit-booking: toast.error("Ezt az időpontot közben valaki lefoglalta. Kérlek, válassz másikat."), clear the selected time and refetch booked slots.
   e) Add a required checkbox above the submit button: "Elolvastam az [Adatkezelési tájékoztatót]." where the bracketed part links to "/adatkezeles" (target _blank). Submit is blocked with toast.error("Kérlek, fogadd el az adatkezelési tájékoztatót.") if unchecked.
5. Keep the existing visual style of the booking page in this prompt (it will be restyled later).

RESULT: Bookings are stored, an already taken slot cannot be booked again, and the form has the privacy acknowledgement.
```
**Ellenőrzés:** foglalj le egy próbaidőpontot, majd töltsd újra az oldalt. Az az időpont most „Foglalt”. Utána **töröld a próbafoglalást** a Lovable Cloud → Database → bookings táblából.

---

## A11 · Segítség oldal: ne ígérjen nem létező űrlapot

```
CONTEXT: On /segitseg (src/pages/SupportPage.tsx) two FAQ answers send the visitor to "a problémabejelentő", but no such form exists. The section title is "Probléma bejelentése" and the lead says "Írd le, miben akadtál el – azonnal válaszolok.", although it is a chatbot that cannot file tickets.

ACTION:
1. Import CONTACT_EMAIL from "@/lib/contact".
2. Update SUPPORT_ITEMS answers:
   - "Nem kaptam visszaigazoló e-mailt. Mit tegyek?" → "Nézd meg a spam vagy promóciók mappát is. Ha 24 óra után sincs meg, írj a {CONTACT_EMAIL} címre."
   - "Módosíthatom vagy lemondhatom az időpontomat?" → "Igen. Írj minél előbb a {CONTACT_EMAIL} címre, és egyeztetünk egy új időpontot."
   - "Milyen adatokat kezeltek rólam?" → "Csak azt, ami a foglaláshoz szükséges: nevet, e-mail-címet és az általad megadott üzenetet. A részleteket az Adatkezelési tájékoztató tartalmazza. Kérésedre törlöm őket." (make "Adatkezelési tájékoztató" a link to /adatkezeles if the answer renderer allows JSX; otherwise keep plain text)
   - Replace "töröljük" / "kezeltek" style plural wording with first person singular in all answers.
3. Header lead: "Nézd meg a gyakori kérdéseket. Ha nem találod a választ, kérdezd meg a chatbotot, vagy írj nekem e-mailt."
4. Rename section title "Probléma bejelentése" → "Kérdezz a chatbottól". Replace the lead line with: "Ügyintézési kérdésekben azonnal válaszol. Ha személyes segítség kell, írj a {CONTACT_EMAIL} címre – 24 órán belül válaszolok." (the email is a mailto link in var(--term-accent-blue)).
5. Check the active rows of the support_answers table: if any answer mentions "problémabejelentő" or "bejelentő", list them in your reply (do not change them automatically).

RESULT: The support page only promises what actually exists.
```
**Ellenőrzés:** a /segitseg oldalon sehol nem szerepel a „problémabejelentő” szó.

---

## A12 · Rólam: üres helyek kitöltése, alternatív szöveg, elírás, gyenge szám

```
CONTEXT: src/components/site/About.tsx (used on /about) renders an empty badge ({""}) and two empty paragraphs ({"\n"}) right next to the portrait. The portrait alt text says "független pénzügyi tanácsadó" (financial advisor), which is a regulated term and contradicts the footer disclaimer. In src/pages/AboutPage.tsx there is a typo "ezelet" and a stat "100% Adatalapú döntés" that is not verifiable.

ACTION:
1. About.tsx:
   - Empty mono line above the H1 → "// Rólam"
   - Badge in the right column ({""}) → "Kovács Rajmond · alapító"
   - Intro paragraph ({"\n"}) → "2024 májusában stratégia nélkül, érzelmi alapon fektettem be először – és veszítettem. Azóta minden ügyletemet előre rögzített szabályok szerint kötöm, és nyilvános naplóban vezetem, a veszteségeket is."
   - Closing paragraph ({"\n"}) → "Abban segítek, hogy te ne a saját pénzeden tanuld meg ugyanezt."
   - Image alt → "Kovács Rajmond, a Rajmi Investments alapítója"
   - Bottom band text → "Ha szeretnéd átbeszélni a saját helyzetedet, " + highlighted "foglalj egy ingyenes 30 perces konzultációt" + "."
   - CTA button label "Időpontfoglalás" → "Ingyenes 30 perces konzultáció"
2. AboutPage.tsx:
   - "Sok pofont kaptam már a piactól, segítek neked elkerülni ezelet" → "Sok pofont kaptam már a piactól. Segítek, hogy te elkerüld ezeket."
   - In the stat strip replace { target: 100, suffix: "%", label: "Adatalapú döntés" } with the number of public dated trades: import { datedTrades } from "@/components/site/TradeResults" and use { target: datedTrades.length, suffix: "", label: "Nyilvános trade" }. Make the label a link to "/eredmenyek".

RESULT: No empty boxes on the About page, compliant wording, and a verifiable stat instead of "100%".
```
**Ellenőrzés:** a /about oldalon a fotó mellett nincs üres keret, a statisztikasávban „93 · Nyilvános trade” látszik.

---

## A13 · A hamis „1 új üzenet” jelzés eltávolítása

```
CONTEXT: src/components/site/ChatNotificationBadge.tsx shows a red pulsing "1" badge over the chat launcher 8 seconds after page load, with the screen-reader text "Új üzeneted érkezett a chatben" – but no message actually arrived. This is a dark pattern and undermines trust.

ACTION: Remove <ChatNotificationBadge /> and its import from src/App.tsx and delete src/components/site/ChatNotificationBadge.tsx. Do not change the Voiceflow widget itself.

RESULT: No fake notification on the site.
```
**Ellenőrzés:** 10 másodperc várakozás után sem jelenik meg piros „1” a chat ikonján.

---

# 🟡 B – A meggyőzőerőhöz

## B1 · Új főoldali szekció: „Ismerős?” + a te történeted

```
CONTEXT: The homepage has no story and does not address the real fears of beginners. The strongest asset of the brand – the founder's story ("Szerencsejátékosból tudatos befektető", currently only on /about) – is missing from the homepage.

ACTION:
1. Create src/components/site/RecognitionStory.tsx, dark terminal style (term-* tokens), two columns on desktop (lg:grid-cols-[1.1fr_0.9fr], gap 64px), stacked on mobile. Section padding like other homepage sections (class "section").
   LEFT column:
   - Mono label (11px, letter-spacing 2px, var(--term-accent-blue)): "// ISMERŐS?"
   - H2 Playfair Display 800, clamp(28px,4vw,48px): "Szeretnél befektetni, de…"
   - Four quote rows (each: left border 2px var(--term-border-accent), padding 14px 18px, Inter 17px, color var(--term-text-primary), italic quotes „…”, 12px gap):
     „…nem értek hozzá, és félek, hogy rosszul döntök."
     „…láttam, mennyien buknak el – nem akarok közéjük tartozni."
     „…nem tudom, kinek higgyek: mindenki el akar adni valamit."
     „…nincs időm egész nap grafikonokat nézni."
   RIGHT column (a card: background var(--term-bg-surface), border 1px var(--term-border-subtle), border-radius 12px, padding 32px):
   - Small round portrait (96px, use "@/assets/portrait-2.jpg", object-cover, border 1px var(--term-border-accent)), alt "Kovács Rajmond".
   - H3 Playfair 800 24px: "Én is itt kezdtem."
   - Paragraph (Inter 16px, line-height 1.75, muted): "2024-ben stratégia nélkül fektettem be, és veszítettem. Nem a piac volt az ellenségem, hanem a saját döntéseim. Megtanultam a kockázatkezelést, szabályokat állítottam fel magamnak, és azóta minden ügyletemet nyilvánosan vezetem – a veszteségeket is."
   - Paragraph (Inter 16px, var(--term-text-primary), font-weight 600, margin-top 12px): "Most abban segítek, hogy te ezt megúszd."
   - Link to "/about" (term-mono 13px, var(--term-accent-blue)): "Az egész történetem →"
   Entrance: simple fade-up (0.45s), quotes stagger 0.08s, respect prefers-reduced-motion. No typewriter, no delays above 0.5s.
2. In src/pages/Index.tsx insert it directly after <HeroTerminal />, wrapped in a SequencedSection and a band div, BEFORE the trades block. Renumber all SequencedSection indices to be consecutive from 1 and keep the band backgrounds alternating.

RESULT: Right after the hero, the visitor recognises their own fears and meets the founder's honest story.
```
**Ellenőrzés:** a főoldalon a hero után azonnal az „Ismerős?” rész jön, a fotóddal.

---

## B2 · Új főoldali szekció: „Mit kapsz, és mennyiért?”

> **Előtte döntsd el:** végleges-e a **24 900 Ft**. Ha vállalsz **valós, határidős ajánlatot** (pl. „az első 10 ügyfélnek 19 900 Ft december 31-ig”), írd be a `[[…]]` helyére. Ha nem, töröld ki a prompt 4. pontját. **Csak akkor írj határidőt, ha tényleg be is tartod.**

```
CONTEXT: The homepage never says what the visitor actually gets and what it costs; the package and price only appear at the bottom of /process (offer panel in src/pages/ProcessPage.tsx). Note: the wording "személyre szabott terv" can be read as personalised investment advice, which requires a licence – avoid it on the homepage.

ACTION:
1. Create src/components/site/OfferSection.tsx (term-* tokens, class "section", max-w 960px centered):
   - Mono label "// AJÁNLAT", H2 Playfair 800 clamp(28px,4vw,48px): "Mit kapsz, és mennyiért?"
   - A 4-step row (grid 1 col mobile / 4 cols desktop, connected by a thin horizontal line on desktop). Reuse the step names and durations from ProcessPage.tsx (01 Ingyenes konzultáció · 30 perc, 02 Helyzetelemzés · 60 perc, 03 …, 04 Követés és finomítás · +30 nap), BUT rename step 03 to "Írásos összefoglaló" (instead of "Személyre szabott terv"). Each step: number (term-mono, blue), title (Inter 600 17px), duration (mono 12px muted).
   - A price card (border 1px var(--term-border-accent), radius 12px, padding 32px, text-center): price "[[24 900 Ft]]" (term-mono 44px, var(--term-text-primary)), "egyszeri díj · nincs előfizetés" (muted mono 13px), then the package contents copied verbatim from the ProcessPage offer panel so they never contradict each other, then one line: "Nem kapok jutalékot semmilyen pénzügyi terméktől – csak tőled kapom a díjat." (Inter 15px, var(--term-accent-green)).
   - Primary button to "/booking": "Ingyenes 30 perces konzultáció →" (same style as the hero primary button), microcopy under it: "Az első 30 perc mindig ingyenes. Utána döntöd el, kéred-e a csomagot."
2. [[OPTIONAL – only if you really offer it]] Above the price card show a small amber badge (var(--term-accent-amber)): "[[Alapító ügyfeleknek: az első 10 ügyfélnek 19 900 Ft – 2026. december 31-ig]]".
3. In src/pages/Index.tsx insert OfferSection after the inflation section and before FinancialQuiz, wrapped in SequencedSection + band div. Renumber indices consecutively and keep band backgrounds alternating.
4. In src/pages/ProcessPage.tsx rename the step "Személyre szabott terv" to "Írásos összefoglaló" as well, so both pages match.

RESULT: The offer and price are visible on the homepage, consistent with the Process page, without advice-like wording.
```
**Ellenőrzés:** a főoldalon, az önteszt előtt látszik az ár és a 4 lépés, ugyanazokkal az adatokkal, mint a Folyamat oldalon.

---

## B3 · Mini-GYIK + záró felhívás a főoldal végén

```
CONTEXT: The homepage currently ends with the self-test. The most common objections are not answered before the footer, and there is no final call to action.

ACTION:
1. Create src/components/site/HomeFaqCta.tsx (term-* tokens, class "section", max-w-3xl centered). Reuse the accordion row style of the FaqRow component in src/pages/SupportPage.tsx (Plus icon rotating to 45°, height animation). First item open by default.
   - Mono label "// GYAKORI KÉRDÉSEK", H2 Playfair 800: "Mielőtt döntesz"
   - Items:
     Q: "Mennyibe kerül?" A: "Az első 30 perces konzultáció ingyenes, és semmire nem kötelez. Ha utána együtt dolgozunk, a mentorcsomag ára [[24 900 Ft]], egyszeri díj."
     Q: "Mi történik a konzultáción?" A: "Megbeszéljük, hol tartasz, mit szeretnél elérni, és elmondom, hogyan tudok segíteni. Ha úgy látom, hogy nem én vagyok a jó választás, azt is megmondom."
     Q: "Megmondod, mibe fektessek?" A: "Nem. Konkrét befektetési ajánlást nem adok – erre engedély kell. Abban segítek, hogy megértsd a kockázatokat, és saját, fegyelmezett döntési rendszert építs."
     Q: "Kezdőként is érdemes?" A: "Igen, kifejezetten kezdőknek szól. Szakzsargon nélkül magyarázok, és nem kell hozzá előzetes tudás."
     Q: "Miért higgyek neked?" A: "Ne higgy – nézd meg. Minden lezárt ügyletem nyilvános, a veszteségekkel együtt." + link "Teljes trade-napló →" to /eredmenyek.
   - Below the accordion, a closing block (border-top 1px var(--term-border-subtle), padding-top 64px, text-center): H2 Playfair 800 clamp(28px,4vw,44px) "Az első lépés 30 perc.", primary button "Ingyenes 30 perces konzultáció →" to /booking (hero primary style), microcopy "30 perc · online · kötelezettség nélkül".
2. In src/pages/Index.tsx add it as the last section after FinancialQuiz (SequencedSection + band div), renumber indices consecutively, keep bands alternating.
3. Also link "Teljes befektetési GYIK →" to /faq under the accordion (term-mono 13px, blue).

RESULT: The homepage ends by answering the main objections and with one clear next step.
```
**Ellenőrzés:** a főoldal az „Az első lépés 30 perc.” blokkal és a gombbal zárul, közvetlenül a lábléc előtt.

---

# ⚪ C – Csiszolás

## C1 · A foglalási oldal az oldal színvilágában

```
CONTEXT: src/pages/BookingPage.tsx uses its own green palette (#0b0f0e, #111816, #1fc98a, #f0ede8, #7a8c87, #3d4f49, #182420, #061a11) and Inter only, so it looks like a different website from the rest (dark terminal: term-* tokens, Playfair Display 800 headings, JetBrains Mono labels, blue primary accent).

ACTION: Restyle only (do not change logic, slots, validation, booked-slot handling or the consent checkbox):
- #0b0f0e → var(--term-bg-base); #111816 → var(--term-bg-surface); #182420 (hover) → rgba(56,189,248,0.06)
- #1fc98a (selection, focus, dots, submit, check icon) → var(--term-accent-blue); #061a11 (text on accent) → #080d14
- #f0ede8 → var(--term-text-primary); #7a8c87 → var(--term-text-muted); #3d4f49 → rgba(255,255,255,0.35)
- border-white/[0.07] / border-white/10 → var(--term-border-subtle); focus border → var(--term-border-accent)
- H1 "Foglalj időpontot": fontFamily var(--font-display), weight 800. Small labels (eyebrow, field labels, weekday headers, "Elérhető időpontok", slot times): term-mono.
- Submit button: same look as the hero primary button (hero-terminal-primary term-mono), full width.
- Success state: CheckCircle2 in var(--term-accent-green) (green = success is fine), heading Playfair 800.

RESULT: The booking page visually belongs to the same site.
```
**Ellenőrzés:** a /booking oldal kék kiemelésű és sötét, mint a főoldal.

---

## C2 · A GYIK oldal az oldal színvilágában

```
CONTEXT: src/pages/FaqPage.tsx uses a different visual language (Fraunces font and a gold palette) than the rest of the site.

ACTION: Restyle only, keep all questions and answers unchanged:
- Remove Fraunces and all gold/yellow colours. Use term-* tokens: background var(--term-bg-base), text var(--term-text-primary)/var(--term-text-muted), accent var(--term-accent-blue).
- Header: mono eyebrow "// BEFEKTETÉSI GYIK" (13px, letter-spacing 0.3em, blue), H1 Playfair Display 800 clamp(36px,5vw,60px) – same structure and spacing as the header of src/pages/SupportPage.tsx.
- Accordion: use exactly the FaqRow look from SupportPage.tsx (18px question, 16px muted answer, blue Plus icon rotating 45°).
- Under the list add: "Ügyintézési kérdésed van? → Segítség" linking to /segitseg (mirror of the link on the support page).
- If the page has its own CTA, use the hero primary button style with the label "Ingyenes 30 perces konzultáció →".

RESULT: /faq and /segitseg look like siblings.
```
**Ellenőrzés:** a /faq oldalon nincs arany szín, és ugyanúgy néz ki, mint a /segitseg.

---

## C3 · Emojik cseréje és egységes gombfeliratok

```
CONTEXT: Emojis clash with the terminal style: the CTA panel in src/components/site/Hero.tsx (✅ 🕐 💻) and the "Az utam" timeline in src/pages/AboutPage.tsx (🎒 ⚠️ 📚 💡 🎯). The primary booking button also has many different labels across the site.

ACTION:
1. Hero.tsx CtaSection: replace the emoji icons with lucide-react icons (Check, Clock, Monitor), size 20, color var(--term-accent-green), inside the existing round badge. Change the button label "Időpont foglalása" → "Ingyenes 30 perces konzultáció" (keep the arrow), and remove textTransform uppercase and letterSpacing 2 from that button so it matches the hero button text style.
2. AboutPage.tsx timeline: remove the emoji span and the `emoji` field; keep the 01–05 numbers and titles.
3. src/components/site/InflationRealValue.tsx: change the CTA label "Megvédem a tőkémet →" → "Ingyenes 30 perces konzultáció →".
4. Leave the form submit button on /booking ("Időpont foglalása →") and the Process page button ("Időpontot választok") unchanged – they answer a different context.

RESULT: No emojis in the UI, and the primary booking CTA has one consistent label everywhere.
```
**Ellenőrzés:** az oldalon sehol nincs emoji, és a fő gomb mindenhol „Ingyenes 30 perces konzultáció” feliratú.

---

## C4 · Gyorsabb animáció az inflációs blokkban

```
CONTEXT: In src/components/site/InflationRealValue.tsx content is held back for too long: the heading subtitle appears after 2.5s, and after the cards the verdict appears at +1.2s, the answer at +3.2s and the CTA at +5.2s. Fast scrollers see empty space.

ACTION: Change only the timings (keep all animation types, the converging arrow and the reduced-motion handling):
- heading subtitle delay: 2.5s → 0.4s
- verdict ("Minden nap, amit vársz, többe kerül."): +1.2s → +0.6s after the cards
- answer ("A döntés a tiéd."): +3.2s → +1.1s
- CTA: +5.2s → +1.6s
- Make the converging arrow draw within the same window (finish before the verdict appears).

RESULT: The whole inflation scene completes in under ~2.5 seconds.
```
**Ellenőrzés:** az inflációs blokkhoz görgetve a gomb kb. 2 másodpercen belül megjelenik.

---

## Ami nem promptfeladat, hanem a tiéd

- **Frissítsd a trade-naplót**: júliusi a legutolsó bejegyzés. Ha van újabb lezárt trade, küldd el, és megírom a promptot, ami beírja őket.
- **A 8 dátum nélküli BTC/MSTR trade dátuma**, és két valószínű elírás (2025.05.15 VIRTUAL, 2025.05.29 SYM; valószínűleg 2026).
- **Vélemények**: az első ügyfelektől kérj írásos visszajelzést, a megjelenítéshez írásos hozzájárulással.
- **Jogász**: az A7–A9-es szövegeket és a Folyamat oldal szóhasználatát nézesse át élesítés előtt.
