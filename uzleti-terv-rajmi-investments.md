# Üzleti terv – Rajmi Investments

*Készült: 2026. október 3.*
*Alap: a Lovable-projekt („Rajmi Investments”, `b474d108-…`) aktuális kódja és tartalma, valamint a „Futtasuk fel cégünket a ChatGPT-vel” fejezet üzletiterv-sablonja.*

> **A tervező szerepe:** közgazdászként és üzleti tervezőként a weboldalon *ténylegesen szereplő* termékekből, számokból és funkciókból indultam ki. Ahol a projekt nem tartalmazott adatot (árak, jogi forma, indulási dátum), ott konkrét javaslatot teszek, és ezt jelölöm (**[javaslat]**). Ahol bizonytalan, külső tényen alapuló adatot használok, azt **[ellenőrizendő]** jelzéssel láttam el.

---

## 0. Vezetői összefoglaló (1 percben)

A Rajmi Investments egy egyszemélyes, online, magyar nyelvű **pénzügyi edukációs és befektetési mentorszolgáltatás** kezdő és haladó magánbefektetőknek. Az alapító, Kovács Rajmond, 2024 óta kereskedik; a weboldal átláthatóan közzéteszi a saját trade-naplóját (101 lezárt ügylet a kódban), ami a márka fő bizalmi eleme.

- **Belépési pont:** ingyenes, 30 perces online konzultáció (a foglalási rendszer már működik).
- **Bevételi modell [javaslat]:** fizetős 1:1 mentorcsomagok + havidíjas elemzői közösség + (2. évtől) online kurzus.
- **Kapacitás:** havonta legfeljebb 5 új 1:1 ügyfél (a weboldal ezt már kommunikálja).
- **Pénzügyi cél [javaslat, kezdő projekthez igazított alacsony árakkal]:** 1. év ≈ 1,9 M Ft, 3. év ≈ 14 M Ft árbevétel; az 1. év nagyjából nullszaldós, a cél ekkor az első ügyfelek, valódi referenciák és az alapító tagok megszerzése.
- **Legnagyobb kockázat:** a **szabályozás**. A „személyre szabott portfólió – mibe, mennyit” típusú szolgáltatás Magyarországon engedélyköteles befektetési tanácsadásnak minősülhet. Ezért a terv az indulást **oktatási jellegű** szolgáltatásra építi, és párhuzamosan kiépíti a jogszerű tanácsadói státuszt (részletek: 7. fejezet).

---

## 1. Vállalati összefoglaló

**Vállalat neve és helye**
- Név: **Rajmi Investments** (márkanév; a weboldal logója: „RAJMI / INVESTMENTS”).
- Működés helye: Magyarország, **teljesen online** (a konzultációk videóhívásban zajlanak; a foglalási felület hétköznap 9:00–17:00 közötti idősávokat kínál).
- Webes jelenlét: a Lovable-ben épített oldal (React + TypeScript + Supabase). **Még nincs publikálva** – az élesítés az indulás első lépése.

**Misszió**
> „Segítek, hogy a megtakarításaid ne az inflációt finanszírozzák, hanem fegyelmezett, adatalapú stratégiával dolgozzanak érted – gyors meggazdagodás ígérete nélkül.”

Ez a weboldal két kulcsüzenetéből áll össze: *„Nem gyors meggazdagodást ígérek”* és *„Szignálok, amelyek mögött adat van – nem megérzés.”*

**Alapítók**
- **Kovács Rajmond** – egyéni alapító, piaci kereskedő 2024 óta.
- Szakmai háttér (a „Rólam” oldal alapján): 2024 májusában kezdett befektetni, az első, stratégia nélküli időszakban veszteséget szenvedett, ebből tanulva épített fel strukturált rendszert: kötelező stop-loss minden pozíción, előre rögzített be- és kilépési szint, minimum 1:2 kockázat/hozam arány.
- Végzettség a weboldal szerint: „Pénzügy és közgazdaságtan”, „Compliance képzés”, „Tanúsított tanácsadó (folyamatban)”. **[ellenőrizendő – ezeket konkrét intézménnyel/oklevéllel érdemes alátámasztani.]**
- Erősség: hiteles „hibáimból tanultam” történet, átlátható trade-napló, a célcsoporttal azonos korosztály és nyelv.
- Hiányosság: rövid (≈2,5 év) piaci múlt, nincs még igazolt szakmai minősítés.

**Jogi forma [javaslat]**
- **Indulás: egyéni vállalkozó** (bejegyzés Ügyfélkapun/webes felületen, díjmentes).
  - Adózás: **átalányadó** (szolgáltatásnál jellemzően 40% költséghányad) vagy – ha kizárólag magánszemélyeknek számláz – **KATA** (havi 50 000 Ft, éves 18 M Ft bevételi korlát). **[ellenőrizendő a 2026–2027-es szabályok szerint, könyvelővel.]**
  - Alanyi ÁFA-mentesség választása, amíg a bevétel az értékhatár alatt marad. **[értékhatár ellenőrizendő.]**
- **4. évtől (≈ 18–20 M Ft bevétel felett): Kft.** – korlátolt felelősség, társasági adó + osztalék, és ez a forma szükséges lehet egy későbbi engedélyes tevékenységhez vagy partnerséghez is.

**Indulás ideje [javaslat]**
| Mérföldkő | Dátum |
|---|---|
| Jogi konzultáció (Bszt./MiCA-megfelelés), ÁSZF, adatkezelési tájékoztató | 2026. október |
| Weboldal javítása és publikálása (lásd 8. fejezet) | 2026. október vége |
| Egyéni vállalkozás bejegyzése, számlázó- és fizetési rendszer | 2026. november 1. |
| Első fizetős ügyfelek (soft launch) | 2026. november |
| Közösség megnyitása alapító tagoknak (várólista nélkül) | az oldal publikálásakor |
| Online fizetés bekötése | később, a tulajdonos döntése szerint |

---

## 2. Termékek és szolgáltatások

### 2.1 A weboldalon jelenleg szereplő kínálat
A „Mit ajánlok?” blokk négy szolgáltatást nevez meg, **ár nélkül**:

| # | Szolgáltatás (weboldal szerint) | Jogi besorolási kockázat |
|---|---|---|
| 1 | **Személyre szabott portfólió** – „mibe, mennyit, milyen arányban” | ⚠️ **Magas** – ez tipikusan befektetési tanácsadás |
| 2 | **Portfólió-elemzés** – írott elemzés konkrét lépésekkel | ⚠️ Magas, ha konkrét pénzügyi eszközre vonatkozó ajánlást tartalmaz |
| 3 | **Pénzügyi alapok érthetően** – kezdőknek | ✅ Alacsony – oktatás |
| 4 | **Egyéni stratégia** – nagy döntések (lakás, vállalkozás, nyugdíj) | Közepes – általános pénzügyi tervezésként jogszerűen nyújtható |

Ezen felül a hero szekció **„Szignálok”**-at és „Csatlakozom” gombot hirdet, de a gomb jelenleg csak a konzultációfoglalásra mutat – **szignálszolgáltatás mint termék még nincs kidolgozva.**

### 2.2 Javasolt termékportfólió és árazás [javaslat]

Az árakat úgy állítottam be, hogy egy 20–35 éves, átlagos jövedelmű magyar célügyfél számára elérhetőek legyenek, és az első évben a kapacitáskorlát (5 új ügyfél/hó) mellett is fenntartható bevételt adjanak.

| Termék | Tartalom | Ár (bruttó) | Státusz |
|---|---|---|---|
| **Ingyenes konzultáció** | 30 perc online, igényfelmérés | 0 Ft | Kész (foglalórendszer működik) |
| **Stratégiai óra** | 60 perc, egy konkrét kérdés (pl. TBSZ, ETF vs. alap, vésztartalék) | 7 900 Ft | Indításra kész |
| **„Alapoktól a rendszerig” mentorcsomag** | 4 × 60 perc 1:1 + írásos összefoglaló + 30 nap e-mailes kérdés | 24 900 Ft | Indításra kész |
| **Portfólió-átvilágítás (oktatási formában)** | A meglévő portfólió költség-, diverzifikációs és kockázati szempontú elemzése, *konkrét vételi/eladási ajánlás nélkül* | 12 900 Ft | Indításra kész, jogi szövegezéssel |
| **Elemzői közösség (Discord/Telegram)** | Heti piaci összefoglaló, saját trade-napló valós időben, oktató élő adások; nem személyre szabott | **Alapító tagság:** első hónap ingyenes, utána 2 990 Ft/hó; később új tagoknak 4 990 Ft/hó | az oldal publikálásakor |

**Fejlesztés alatt álló termékek**
| Termék | Leírás | Tervezett indulás | Ár |
|---|---|---|---|
| **Online videókurzus** | „Fegyelmezett befektető” – 8 modul: kockázatkezelés, pozícióméretezés, pszichológia, TBSZ/NYESZ, ETF-ek | 2027. Q2 | 14 900 Ft |
| **Tagi felület a weboldalon** | Supabase-alapú bejelentkezés, kurzus- és közösségi tartalmak egy helyen (az Auth és az adatbázis már adott) | 2027. Q2 | – |
| **Élő trade-napló** | A jelenleg kódba égetett trade-lista Airtable/Supabase adatbázisból töltődik (az Airtable-integráció már létezik) | 2026. Q4 | – |
| **Hírlevél** | Heti piaci összefoglaló; az e-mail-infrastruktúra (sor, leiratkozás, suppression) már kész | 2026. Q4 | ingyenes (lead) |
| **Vállalati workshop** | Pénzügyi tudatosság KKV-k és cégek munkavállalóinak | 2028 | 120 000 Ft/alkalom |
| **Engedélyes tanácsadás** | Valódi, személyre szabott befektetési tanácsadás – csak engedély/függő ügynöki státusz után | 2028– | 2. fázis |

**Szolgáltatások (kiegészítők)**
- Ingyenes interaktív eszközök a weboldalon (már elkészültek): pénzügyi önteszt (kvíz), befektetési kalkulátor, inflációs/reálérték-szimulátor, részletes GYIK (TBSZ, NYESZ, OBA, BEVA, adózás).
- Csevegő widget („Talk to AI”/„Segíthetek?”) gyors kérdésekhez.

---

## 3. Piaci elemzés

### 3.1 Célpiac

**Elsődleges szegmens – „a bizonytalan megtakarító”**
- **Kor:** 20–35 év
- **Nem:** jellemzően férfi többség (a tőzsde- és kriptoközönség ilyen), de a kommunikáció legyen semleges
- **Életstílus:** online-first, mobilon tájékozódik (TikTok, Instagram, YouTube), tanuló vagy pályakezdő/fiatal szakember (IT, mérnök, egészségügy, kereskedelem)
- **Jövedelem:** nettó 350 000 – 900 000 Ft/hó; megtakarítás 0,5–10 M Ft, jellemzően bankszámlán vagy állampapírban
- **Földrajz:** Budapest és megyei jogú városok; mivel minden online, az egész magyar nyelvterület (a határon túli magyarok is)

**Másodlagos szegmens – „a csalódott kezdő trader”**
- 18–30 év, már próbálkozott kriptóval/tőzsdével, veszített; strukturált rendszert keres. Pontosan az alapító saját története – erre a legerősebb a márkaüzenet.

**Harmadlagos szegmens (3. évtől)** – kisvállalkozók és cégek HR-osztályai (pénzügyi tudatossági workshopok).

### 3.2 Piaci igények – és hogyan felel meg nekik a vállalkozás

| Igény | Válasz a Rajmi Investments részéről |
|---|---|
| „Félek, hogy az inflációtól elolvad a pénzem” | Inflációs és megtakarítási szekciók, kalkulátor → konkrét első lépések |
| „Nem tudom, hol kezdjem, túl bonyolult” | „Pénzügyi alapok érthetően”, magyar GYIK, mentorcsomag |
| „Nem bízom a bankban, mert termékeket akar eladni” | Független, jutalékmentes, termékértékesítés nélküli modell |
| „Nem bízom a ’guruk’-ban sem” | Nyilvános trade-napló a veszteséges ügyletekkel együtt, „nem ígérek gyors meggazdagodást” |
| „Egyedül érzelmi döntéseket hozok” | Szabályalapú rendszer (stop-loss, 1:2 R/R), közösség, elszámoltathatóság |

### 3.3 Versenytársak

*(A konkrét szereplők példaként szerepelnek; a lista az indulás előtt frissítendő. **[ellenőrizendő]**)*

| Kategória | Példák | Erősségük | Gyengeségük | Rajmi pozíciója velük szemben |
|---|---|---|---|---|
| Banki/brókeri tanácsadás | Nagybankok és brókercégek befektetési tanácsadói | Engedély, bizalom, intézményi háttér | Termékértékesítési érdek, személytelen | Független, közérthető, a fiatalok nyelvén |
| Ingyenes pénzügyi tartalom | Pénzügyi blogok és portálok (pl. Kiszámoló, Bankmonitor, Portfolio.hu) | Nagy elérés, ingyenes, hiteles | Nem személyes, nincs mentorálás | 1:1 figyelem, közösség |
| Finfluencerek | Magyar YouTube/TikTok pénzügyi tartalomgyártók | Nagy közönség | Gyakran nem átlátható eredmények, szponzorált tartalom | Teljes, auditálható trade-napló |
| Szignálcsoportok | Telegram/Discord kripto- és tőzsdecsoportok (gyakran külföldiek) | Olcsók, gyorsak | Sokszor hamis eredmények, nulla oktatás, magas csalási kockázat | Kockázatkezelés-központú, oktatással egybekötött |
| Online kurzusplatformok | Nemzetközi kurzusok (angol nyelvű) | Mélység, olcsó | Nem magyar adózás, nincs személyes támogatás | Magyar szabályozás (TBSZ, NYESZ, SZJA) + mentor |

### 3.4 SWOT-analízis

| **Erősségek (S)** | **Gyengeségek (W)** |
|---|---|
| • Nyilvános, részletes trade-napló (101 ügylet, veszteségekkel együtt) | • Rövid, ≈2,5 éves piaci tapasztalat |
| • Kész, igényes, „dark fintech terminal” arculatú weboldal foglalórendszerrel, e-mail-automatizálással, kvízzel és kalkulátorral | • Nincs igazolt szakmai minősítés / engedély |
| • Hiteles személyes történet („szerencsejátékosból tudatos befektető”) | • Egyszemélyes vállalkozás – a kapacitás az alapító ideje |
| • Alacsony fix költség, teljesen online működés | • A weboldalon jelenleg pontatlan/helykitöltő elemek vannak (lásd 8. fejezet) |
| • Kockázatkezelés-központú, „nem ígérek” üzenet | • Az eredmények rövid időszakot fednek le, pozícióméret nélkül |
| **Lehetőségek (O)** | **Veszélyek (T)** |
| • Magas infláció után megnőtt a lakossági érdeklődés a befektetés iránt | • **Szabályozás:** Bszt. (befektetési tanácsadás), MiCA (kriptoeszköz-tanácsadás), MAR (befektetési ajánlások), MNB finfluencer-elvárásai |
| • A TBSZ/NYESZ és az ETF-ek iránti kereslet – magyar nyelvű, érthető tartalom hiánya | • Egy rossz piaci időszak (drawdown) rombolja a nyilvános eredménysort |
| • Rövid videós platformok olcsó elérést adnak a célcsoporthoz | • Hirdetési platformok korlátozzák a pénzügyi hirdetéseket |
| • Később partnerség engedélyes szolgáltatóval (függő ügynöki státusz) | • A „szignál”-piac rossz hírneve – összemosás a csalókkal |
| • B2B pénzügyi tudatossági képzések | • Kiégés / időhiány (egyszemélyes modell) |

---

## 4. Marketing és értékesítési stratégia

### 4.1 Pozicionálás
> **„Az átlátható befektetési mentor – aki megmutatja a veszteségeit is.”**

- **Kategória:** független pénzügyi edukáció és mentorálás (nem bank, nem guru, nem szignálbolt).
- **Fő ígéret:** fegyelmezett, adatalapú rendszer – nem hozamgarancia.
- **Bizonyíték:** nyilvános trade-napló, „Amit nem kínálok” lista (nincs gyors meggazdagodás, nincs hype).
- **Hangnem:** egyenes, tegező, fiatalos, de nem harsány. A jelenlegi sürgető elemeket („Valaki most foglalja el azt a helyet…”, „Cselekedj még ma!”) érdemes visszafogni, mert ütköznek a „nyugodt, fegyelmezett” márkaképpel, és a fogyasztóvédelmi szabályok szerint is kockázatosak lehetnek.

### 4.2 Marketingstratégia

**Online**
| Csatorna | Taktika | Gyakoriság | KPI |
|---|---|---|---|
| TikTok / Instagram Reels / YouTube Shorts | „Ma ezt a trade-et zártam – miért léptem ki” rövid videók; mítoszrombolás; infláció-kalkulátor bemutató | heti 3–4 db | követők, profilkattintás |
| YouTube (hosszú) | Havi „trade-napló értékelés” + TBSZ/ETF magyarázó videók | havi 2 db | feliratkozó, nézési idő |
| Hírlevél | Heti piaci összefoglaló (az infrastruktúra kész) | heti 1 | megnyitás > 40%, kattintás > 5% |
| SEO / blog | A meglévő GYIK-témák (TBSZ, NYESZ, OBA vs. BEVA, adózás) önálló cikkekké bontása | havi 2 cikk | organikus látogató |
| Lead-mágnesek | Pénzügyi önteszt és befektetési kalkulátor → e-mail-cím megadásával részletes eredmény | folyamatos | konverzió látogató→lead ≥ 8% |
| Fizetett hirdetés | Meta/YouTube kis költségkerettel, kizárólag oktatási tartalom népszerűsítése (pénzügyi hirdetési szabályok betartásával) | 1. év: 50 000 Ft/hó | CPL < 1 000 Ft |
| LinkedIn | Szakmai jelenlét, B2B workshopok előkészítése | heti 1 | – |

**Offline**
- Ingyenes előadások egyetemeken, kollégiumokban, ifjúsági szervezeteknél („Az első 1 millióm befektetése”).
- Workshopok coworking irodákban (Budapest).
- Konferenciák: részvétel hallgatóként, később előadóként befektetői/fintech eseményeken.

**Értékesítési tölcsér (cél, 1. év)**
```
Látogató (havi 3 000)
  → lead (kvíz/kalkulátor/hírlevél) 8% ≈ 240
    → ingyenes konzultáció 5% ≈ 12
      → fizetős 1:1 csomag 25–30% ≈ 3–4 / hó
    → közösségi előfizető (leadből) 2–3% ≈ 5–7 új / hó
```

### 4.3 Értékesítési terv
- **Csatornák:**
  1. **Közvetlen értékesítés** a konzultáción keresztül (fő csatorna az 1:1 csomagokhoz).
  2. **Webáruház / online fizetés** a weboldalon – ⏸ **később** (az oldal még tervezési fázisban van); a `submit-order` funkció és a rendelés-visszaigazoló e-mail már létezik; ehhez Stripe vagy Barion fizetést és automatikus számlázást (Számlázz.hu / Billingo) kell kötni. Az alapértelmezett pénznemet **USD-ről HUF-ra** kell állítani.
  3. **Előfizetés** a közösséghez – az alapító tagok első hónapja ingyenes, a díjfizetés módja később dől el.
  4. **Partnerek (2. évtől):** affiliate-megállapodás más oktatókkal, **de nem** brókerekkel vagy pénzügyi termékekkel (különben sérül a „független, jutalékmentes” ígéret).
- **Ajánlói program:** meglévő ügyfél ajánlása után 1 hónap ingyenes közösségi tagság.
- **Garancia:** mentorcsomagnál az első alkalom után feltétel nélküli visszatérítés.

---

## 5. Operációs terv

### 5.1 „Gyártás” – hogyan és hol készül a szolgáltatás
Mivel szolgáltatásról van szó, a „gyártás” a szolgáltatásnyújtási folyamat:

1. **Lead érkezik** (weboldal, közösségi média, hírlevél).
2. **Foglalás** a `/booking` oldalon → Supabase `submit-booking` funkció → automatikus visszaigazoló e-mail az ügyfélnek + értesítés a tulajdonosnak (mindkét sablon kész).
3. **Ingyenes konzultáció** (30 perc, Google Meet/Zoom) a weboldal 4 lépéses folyamata szerint: konzultáció → helyzetelemzés (1–2 nap) → személyre szabott *oktatási* terv → folyamatos támogatás.
4. **Ajánlat és fizetés** online.
5. **Szolgáltatásnyújtás** – alkalmak, írásos összefoglaló, közösségi tartalmak.
6. **Utókövetés** – elégedettségi kérdőív, valódi ügyfélvélemény (írásos hozzájárulással), ajánlói program.

**Időbeosztás (1. év):** heti ≈ 20 óra – 8 óra 1:1 munka, 6 óra tartalomgyártás, 4 óra piaci elemzés és saját kereskedés, 2 óra adminisztráció.
**Kapacitás:** max. 5 új 1:1 ügyfél/hó (a weboldalon már vállalt korlát), ≈ 15–20 aktív 1:1 alkalom/hó.

### 5.2 Beszállítók és beszerzési stratégia

| Terület | Beszállító | Becsült költség [ellenőrizendő] |
|---|---|---|
| Weboldal-fejlesztés és hosting | Lovable | ≈ 25 USD/hó |
| Backend, adatbázis, auth, e-mail-sor | Supabase (Lovable Cloud) | 0–25 USD/hó |
| CRM / trade-napló adatbázis | Airtable | 0–20 USD/hó |
| Domain + céges e-mail | regisztrátor + Google Workspace | ≈ 60 000 Ft/év |
| Videóhívás | Google Meet / Zoom | 0–6 000 Ft/hó |
| Chartok, piaci adatok | TradingView | ≈ 10 000 Ft/hó |
| Fizetés | Stripe / Barion | tranzakciónként ≈ 1,5–3% |
| Számlázás | Számlázz.hu / Billingo | 0–5 000 Ft/hó |
| Közösségi platform | Discord / Telegram | 0 Ft |
| Könyvelés | egyéni könyvelő | 15 000–25 000 Ft/hó |
| Jogi háttér | pénzügyi szabályozásban jártas ügyvéd | egyszeri 300–500 ezer Ft, utána eseti |

**Beszerzési elvek:** ingyenes vagy olcsó csomagokkal indulni, és csak a bevétel növekedésével lépni magasabb szintre; minden adatkezelő beszállítóval adatfeldolgozói szerződés (GDPR); havi előfizetések negyedéves felülvizsgálata.

### 5.3 Logisztika – „raktározás, szállítás, készletkezelés” digitális megfelelője
- **Raktározás = adattárolás:** ügyféladatok a Supabase-ben (sorszintű jogosultságkezeléssel), heti mentés; adatkezelési tájékoztató és szerződés minden ügyfélnek.
- **Szállítás = tartalomkézbesítés:** e-mail-automatizmus (a meglévő sor + leiratkozás + suppression lista), tagi felület, közösségi szerver.
- **Készletkezelés = idő és kapacitás:** a foglalási idősávok (jelenleg 8 sáv/nap, hétköznap) a valós szabad időhöz igazítva; **jelenleg a rendszer nem zárja ki a már lefoglalt időpontokat** – ezt az élesítés előtt javítani kell, különben dupla foglalás lehet.
- **Tartalomkészlet:** 4 hetes előre legyártott tartalomnaptár (videók, hírlevél), hogy egy betegség vagy vizsgaidőszak ne állítsa le a marketinget.

---

## 6. Pénzügyi terv

*Minden szám **[javaslat]**, bruttó, forintban, konzervatív (bázis) forgatókönyv szerint. A kalkuláció feltételezi az alanyi ÁFA-mentességet az első két évben.*

### 6.1 Kezdeti költségvetés – a vállalkozás elindításához szükséges tőke

| Tétel | Összeg |
|---|---|
| Vállalkozás bejegyzése (egyéni vállalkozó) | 0 Ft |
| Jogi csomag: Bszt./MiCA/MAR megfelelési vélemény, ÁSZF, adatkezelési tájékoztató, kockázati nyilatkozat | 400 000 Ft |
| Szakmai képzés / minősítés megkezdése (pl. tőkepiaci vagy EFPA-képesítés) | 250 000 Ft |
| Technológia első 6 hónapra (Lovable, Supabase, domain, e-mail, TradingView) | 180 000 Ft |
| Eszközök (mikrofon, kamera, világítás a videókhoz) | 150 000 Ft |
| Indulási marketing (3 hónap hirdetés + tartalomgyártás) | 150 000 Ft |
| Arculati finomítás, valódi portréfotók | 50 000 Ft |
| Működési tartalék (≈ 6 hónap fix költség) | 600 000 Ft |
| **Összesen** | **≈ 1 780 000 Ft** |

### 6.2 Pénzügyi előrejelzések – bevételek és kiadások az első 5 évre

**Bevételi feltevések**
| Bevételi forrás | 1. év (2027) | 2. év | 3. év | 4. év | 5. év |
|---|---|---|---|---|---|
| Mentorcsomag (db × átlagár) | 30 × 22 000 | 48 × 24 900 | 55 × 27 900 | 60 × 29 900 | 60 × 32 900 |
| Stratégiai óra (db × ár) | 40 × 7 900 | 60 × 7 900 | 60 × 9 900 | 70 × 9 900 | 70 × 9 900 |
| Közösség (átlagos fizető tag × havidíj × 12) | 25 × 2 990 | 70 × 3 990 (vegyes) | 130 × 4 990 | 180 × 4 990 | 230 × 4 990 |
| Online kurzus (db × 14 900) | – | 120 | 250 | 320 | 400 |
| B2B workshop (db × 120 000) | – | – | 6 | 10 | 14 |

**Eredménykimutatás (millió Ft)**
| | 1. év | 2. év | 3. év | 4. év | 5. év |
|---|---|---|---|---|---|
| Mentorcsomag | 0,66 | 1,20 | 1,53 | 1,79 | 1,97 |
| Stratégiai óra | 0,32 | 0,47 | 0,59 | 0,69 | 0,69 |
| Közösségi tagdíj | 0,90 | 3,35 | 7,78 | 10,78 | 13,77 |
| Online kurzus | – | 1,79 | 3,73 | 4,77 | 5,96 |
| B2B workshop | – | – | 0,72 | 1,20 | 1,68 |
| **Árbevétel összesen** | **1,88** | **6,81** | **14,35** | **19,23** | **24,07** |
| Technológia és szoftver | 0,40 | 0,50 | 0,70 | 0,90 | 1,10 |
| Marketing | 0,60 | 1,20 | 2,00 | 2,50 | 3,00 |
| Könyvelés, jog, biztosítás | 0,50 | 0,60 | 0,80 | 1,00 | 1,20 |
| Képzés, minősítés | 0,25 | 0,30 | 0,30 | 0,30 | 0,30 |
| Fizetési díjak (~2,5%) | 0,05 | 0,17 | 0,36 | 0,48 | 0,60 |
| Külsős segítség (vágó, közösségi moderátor, asszisztens) | – | 0,60 | 1,20 | 2,40 | 3,60 |
| **Működési költség összesen** | **1,80** | **3,37** | **5,36** | **7,58** | **9,80** |
| **Adózás előtti eredmény** | **0,08** | **3,44** | **8,99** | **11,65** | **14,27** |

**Megjegyzések az előrejelzéshez**
- Az eredmény **még nem tartalmazza** az alapító saját bérét/vállalkozói kivétjét és a személyes adókat/járulékokat – ezek a választott adózási formától függnek (KATA/átalányadó/Kft.).
- A 4. évtől a bevétel meghaladja a KATA-korlátot és valószínűleg az alanyi ÁFA-mentesség határát is → **Kft. + ÁFA-kör** szükséges; ekkor a 27%-os ÁFA miatt vagy az árakat kell emelni, vagy a nettó bevétel ≈ 21%-kal csökken. **Ezt a 3. év végén újra kell tervezni.**
- A legnagyobb érzékenység a **közösségi előfizetők számán** van (3. évben a bevétel ≈ 54%-a).

**Forgatókönyvek (3. év árbevétele)**
| Forgatókönyv | Feltevés | Árbevétel |
|---|---|---|
| Pesszimista | Közösség átlag 60 fő, kurzus 100 db, nincs B2B | ≈ 7 M Ft |
| **Bázis** | fenti táblázat | **≈ 14 M Ft** |
| Optimista | Közösség átlag 220 fő, kurzus 400 db, 10 workshop | ≈ 22 M Ft |

**Fedezeti pont:** az 1. év fix költségei (≈ 1,75 M Ft/év ≈ 146 000 Ft/hó) havi **≈ 6 mentorcsomaggal** vagy **≈ 49 fizető alapító taggal** fedezhetők. Az alacsony árak miatt az 1. év célja nem a profit, hanem a referenciák és a közösség felépítése; az árak a 2–3. évtől, valódi eredmények birtokában emelhetők.

### 6.3 Finanszírozási igények
- **Külső finanszírozás nem szükséges.** A ≈ 1,8 M Ft-os indulótőke saját megtakarításból fedezhető (bootstrapping), ami egy pénzügyi oktatónál hitelességi kérdés is: *nem hitelből indul.*
- Ha a saját tőke nem elegendő: az indulás a jogi csomagra (400 000 Ft) és a tartalékra szűkíthető, a marketing a bevételekből finanszírozható → minimális indulótőke ≈ **900 000 Ft**.
- Opcionálisan: fiatal vállalkozóknak szóló állami/uniós induló támogatások (időszakos kiírások – **[ellenőrizendő az aktuális pályázati kínálat]**).
- **Kerülendő:** befektetőtől pénzt bevonni, vagy ügyfelek pénzét kezelni – ez külön engedélyhez kötött tevékenység lenne.

---

## 7. Szabályozási megfelelés és kockázatkezelés (kiemelt fejezet)

> ⚠️ **Nem vagyok jogász; ez a fejezet a kockázatok feltérképezése, nem jogi tanács.** Az indulás előtt pénzügyi szabályozásban jártas ügyvéddel kell egyeztetni.

| Kockázat | Miért fontos | Kezelés |
|---|---|---|
| **Befektetési tanácsadás engedély nélkül** (Bszt. – 2007. évi CXXXVIII. tv.) | Konkrét pénzügyi eszközre vonatkozó, személyre szabott ajánlás (pl. „ebből a részvényből vegyél ennyit”) engedélyköteles befektetési szolgáltatás. A weboldal „Személyre szabott portfólió – mibe, mennyit” szövege ilyennek tűnhet. | 1. fázisban **oktatás és általános pénzügyi tervezés**; a szövegek átírása; később **függő ügynöki** státusz egy engedélyes szolgáltató mellett vagy saját engedély. |
| **Kriptoeszköz-tanácsadás** (MiCA – EU 2023/1114) | A trade-napló jelentős része kripto (SUI, SOL, TAO, ETH, BTC…). A kriptoeszközökkel kapcsolatos tanácsadás MiCA szerint engedélyköteles szolgáltatás. | Kriptóval kapcsolatban kizárólag oktatási, nem személyre szabott tartalom. |
| **Befektetési ajánlások közzététele** (MAR – EU 596/2014) | A nyilvános „jelzések” (trade-ötletek) befektetési ajánlásnak minősülhetnek, ami közzétételi és összeférhetetlenségi szabályokkal jár (pl. saját pozíció feltüntetése). | Minden posztnál: saját pozíció jelzése, időpont, kockázati figyelmeztetés; az MNB finfluencerekre vonatkozó elvárásainak követése. |
| **Fogyasztóvédelem – megtévesztő gyakorlat** (Fttv. – 2008. évi XLVII. tv.) | A weboldalon **kitalált ügyfélvélemények** szerepelnek (az egyik a „Marcus” nevet említi – ez nyilvánvalóan sablonszöveg). Nem létező vélemény közzététele tisztességtelen kereskedelmi gyakorlat. | **Azonnal eltávolítani**; csak valódi, írásos hozzájárulással gyűjtött véleményt használni. |
| **Eredménykommunikáció** | A „LIVE” felirat, a kódba égetett „130 lezárt trade / 56%” és a trade-enkénti átlaghozam félrevezető lehet (lásd 8. fejezet). | Pontos, auditálható számok; módszertani magyarázat; portfólió-szintű hozam közlése. |
| **GDPR** | Ügyféladatok, pénzügyi helyzetre vonatkozó információk kezelése. | Adatkezelési tájékoztató, adatfeldolgozói szerződések, minimális adatgyűjtés. |
| **Felelősség** | Ügyfélveszteség miatti panasz. | ÁSZF felelősségkorlátozással, írásos kockázati nyilatkozat aláíratása; később szakmai felelősségbiztosítás. |
| **Kulcsember-kockázat** | Egyszemélyes vállalkozás. | Előre gyártott tartalom, automatizált e-mailek, 2. évtől külsős segítő. |

---

## 8. A Lovable-projekt jelenlegi állapotából fakadó teendők (indulás előtti javítólista)

A kód áttekintése alapján a következőket javaslom **a publikálás előtt** rendezni:

1. **Kitalált ügyfélvélemények** (`Trust.tsx`): „Hanna B.”, „Dávid K.”, „Sofia M.” – az első szövege „Marcus”-t említi. Eltávolítandó vagy valódi véleményekre cserélendő.
2. **Eredményszámok összhangja** (`HeroTerminal.tsx`): a hero fixen **130 trade-et** és **56%-os** nyerési arányt mutat, de a trade-listában **101 ügylet** van. A lista alapján számolva: 56 nyerő (55,4%), átlag +3,40%/trade, medián +1,62%.
   - A 8 **dátum nélküli** ügylet (7 db BTC azonos 60 000 $-os belépővel + 1 MSTR) mind nyereséges; ezek nélkül 93 ügylet, **51,6%** nyerési arány és **+1,88%** átlag. Ezeket vagy dátummal kell ellátni, vagy külön jelölni.
   - A trade-enkénti átlaghozam pozícióméret nélkül nem azonos a portfólió hozamával – ezt érdemes jelezni.
   - A „LIVE” felirat csak akkor maradjon, ha az adat ténylegesen élőben frissül.
   - Két tételnél valószínű elírás a dátumban (2025.05.15 VIRTUAL, 2025.05.29 SYM – a többi 2025.12.31 utáni).
3. **„Tanúsított tanácsadó (folyamatban)”** és a végzettségek – konkretizálni vagy kivenni.
4. **Domain-eltérés:** a láblécben `info@rajminvestments.com` szerepel, a márkanév viszont „Rajmi**i**nvestments” – egységesíteni.
5. **Foglalási rendszer:** a már lefoglalt időpontok nem tűnnek el – dupla foglalás veszélye.
6. **Rendelési rendszer:** alapértelmezett pénznem USD → HUF; online fizetés bekötése.
7. **Hiányzó jogi oldalak:** ÁSZF, adatkezelési tájékoztató, impresszum (kötelező adatok).
8. **Üres szövegblokkok** az `About.tsx`-ben (badge, bevezető és záró sor jelenleg csak sortörést tartalmaz).
9. **Projekt-knowledge eltérés:** a Lovable-projekt „Knowledge” beállítása egy *alapkezelői platformot* ír le (NAV, alapok, tranzakciók), miközben az oldal személyes mentorszolgáltatás. Érdemes a valós üzleti modellhez igazítani, hogy a Lovable AI ne ebbe az irányba fejlesszen.
10. **Sürgető marketingszövegek** („Valaki most foglalja el azt a helyet…”) – visszafogni a márkaképhez és a fogyasztóvédelmi elvárásokhoz igazítva.

---

## 9. Első 90 nap – cselekvési terv

| Hét | Teendő | Eredmény |
|---|---|---|
| 1–2 | Jogi konzultáció; szövegek átírása oktatási fókuszra; kitalált vélemények törlése | Jogilag biztonságos weboldal |
| 2–3 | Trade-statisztika javítása, ÁSZF/adatkezelés, foglalási ütközés javítása | Publikálható oldal |
| 3–4 | Egyéni vállalkozás bejegyzése, weboldal publikálása (online fizetés később) | Működő, publikus oldal |
| 5–8 | Heti 3 rövid videó, heti hírlevél, kvíz → e-mail lead-gyűjtés | 150+ e-mail-cím |
| 6–10 | Első 5–8 fizetős mentorált; véleményük gyűjtése | Valódi referenciák |
| 5–12 | Közösség indítása (Discord) alapító tagoknak: első hónap ingyenes, utána 2 990 Ft/hó – várólista nélkül | Aktív induló közösség |

**Siker mérése 90 nap után:** ≥ 3 000 látogató/hó, ≥ 150 lead, ≥ 6 fizető ügyfél, ≥ 20 aktív alapító tag a közösségben.

---

*Kockázati figyelmeztetés: ez az üzleti terv tervezési segédanyag. A számok becslések, nem garanciák; a jogi és adózási pontokat szakemberrel kell ellenőrizni.*
