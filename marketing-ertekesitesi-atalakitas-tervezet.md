# Tervezet – a weboldal marketing- és értékesítési részének átalakítása

*Rajmi Investments · Lovable-projekt `b474d108-…` · 2026. október 3.*
*Alap: az üzleti terv 4. fejezete („Marketing és értékesítési stratégia”), a könyv sablonjának három pontja szerint: **Pozicionálás → Marketingstratégia → Értékesítési terv**.*

> **Státusz (2026. október 3.):** az 1. (tisztítás) és a 2. (pozicionálás) fázis elkészült a Lovable-projektben (commit `55ba630`). A 3–6. fázis még tervezet; az online fizetés a tulajdonos döntéséig szünetel.

---

## 0. Röviden: mi a fő gond most, és mi lesz a cél

| | Most | Cél |
|---|---|---|
| **Kinek szól?** | Egyszerre szól a gyors jelzéseket keresőknek („A piac nem vár… te mikor lépsz?”) és óvatos kezdőnek („Nem gyors meggazdagodást ígérek”) | Egy fő célcsoport: **a bizonytalan, 20–35 éves megtakarító**, valamint a „csalódott kezdő trader” |
| **Mit árulunk?** | Négy szolgáltatás **ár nélkül**; a „Csatlakozom” gomb egy ingyenes konzultációra visz | Átlátható **csomagok árakkal**, egyértelmű következő lépéssel |
| **Miért higgyenek nekünk?** | Trade-napló, de pontatlan összesítő számokkal; **kitalált vélemények** | Ellenőrizhető napló, módszertan, valódi történet, később valódi vélemények |
| **Mi a következő lépés?** | Sok, eltérő feliratú gomb („Csatlakozom”, „Belépek most”, „Időpontfoglalás”, „Cselekedj még ma!”) | **Egy fő CTA** mindenhol: „Ingyenes konzultáció foglalása”, mellette **egy** másodlagos: „Ingyenes önteszt” (lead) |
| **Mi történik, ha még nem vásárol?** | Semmi: a kvíz és a kalkulátor végén nincs se e-mail-gyűjtés, se ajánlat | Minden ingyenes eszköz végén e-mail-cím → hírlevél → konzultáció |

---

## 1. POZICIONÁLÁS – hogyan pozicionálom a vállalkozást az oldalon

### 1.1 Pozicionáló mondat (minden szöveg ehhez igazodik)
> **„Az átlátható befektetési mentor – aki a veszteségeit is megmutatja.”**
> Független · Jutalékmentes · Rendszer, nem megérzés.

### 1.2 Hero (főoldal teteje) – `HeroTerminal.tsx`

| Elem | Most | Javaslat |
|---|---|---|
| Főcím | „A piac nem vár.” | **„Befektetés rendszerrel – nem megérzésből.”** |
| Alcím | „A kérdés csak az: te mikor lépsz?” | **„Független, jutalékmentes mentorálás, hogy a megtakarításod ne az inflációt finanszírozza.”** |
| USP-sor | „Szignálok, amelyek mögött adat van – nem megérzés.” | **„Minden trade-emet nyilvánosan vezetem – a veszteségeseket is.”** (A „szignál” szó helyett, ahol a szövegbe illik, „jelzés” áll; ahol nem illik, kimarad.) |
| Elsődleges gomb | „Csatlakozom →” (a foglalásra visz) | **„Ingyenes 30 perces konzultáció →”** |
| Másodlagos gomb | „Megnézem az eredményeket” | **„Hol tartok most? – 2 perces önteszt”** (lead-gyűjtő) |
| Bizalmi sáv (új) | – | Kis ikonsor a gombok alatt: ✓ Független · ✓ Nem árulok pénzügyi terméket · ✓ Havonta max. 5 új ügyfél |
| Eredménydoboz | „LIVE”, fixen beírt 130 trade / 56%, átlag +3,40% | Felirat: **„Trade-napló · frissítve: <dátum>”**; a számok a listából számolódjanak (jelenleg 101 trade, 55%); alatta egy **„Hogyan számolok?”** link. A „LIVE” csak valódi élő adatnál maradjon. |

### 1.3 Az egész oldalra vonatkozó hangnem-szabályok
- **Ki:** hamis sürgetés. Ez a „Valaki most foglalja el azt a helyet, amit te holnapra halasztasz” overlay, ami 2,5 mp után eltakarja a trade-kártyákat, valamint a „Cselekedj még ma!” és a „Belépek most →” felirat.
- **Be:** valós szűkösség („Havonta max. 5 új ügyfél – <hónap>: még X hely”), de csak akkor, ha a szám valós.
- Tegező, nyugodt, konkrét hangnem. Minden állításnak legyen bizonyítéka (napló, folyamat, „Amit nem kínálok”).
- **Szóhasználat (jogi okból):** „személyre szabott portfólió – mibe, mennyit” helyett „**személyre szabott befektetési tanulási terv**”, „ajánlás” helyett „**elemzés, oktatás**”.

---

## 2. MARKETINGSTRATÉGIA – mit csinál az oldal a látogató megszerzéséért

### 2.1 Új főoldali sorrend (értékesítési tölcsér szerint)

**Most** (`Index.tsx`): Hero → Valós eredmények + CTA (overlay) → Megtakarítás-hook → Sokkoló adat → Infláció → Önteszt → Kalkulátor.
*(Megjegyzés: a „Mit ajánlok?” (`Why.tsx`) és a „Bizalom” (`Trust.tsx`) szekció a jelenlegi kódban **nincs a főoldalon**, pedig egy korábbi Lovable-terv ezt késznek jelölte.)*

**Javasolt** (Probléma → Megoldás → Bizonyíték → Ajánlat → Cselekvés):

| # | Szekció | Szerep a tölcsérben | Forrás |
|---|---|---|---|
| 1 | **Hero** (új szöveg, 1.2) | Figyelem + pozicionálás | átírás |
| 2 | **Probléma:** megtakarítás + infláció **egy** rövid szekcióban | Fájdalompont | `SavingsHook` + `InflationRealValue` összevonva, a `ShockDataSection` rövidítve |
| 3 | **Megoldás: „Így dolgozom”** – 3 szabály (stop-loss, előre rögzített szintek, min. 1:2 R/R) | Különbözőség | az `About.tsx` „traits” elemei |
| 4 | **Bizonyíték: trade-napló** – top trade-ek + összesítő + „Teljes napló” gomb | Hitelesség | `Hero.tsx` TradeShowcase, overlay nélkül |
| 5 | **Ajánlat: „Csomagok”** (ÚJ, 3.1) | Döntés | új komponens |
| 6 | **Folyamat** – 4 lépés tömören | Kockázatcsökkentés („mi fog történni?”) | `Process.tsx` rövid változata |
| 7 | **Rólam röviden** – fotó + „szerencsejátékosból tudatos befektető” + link | Személyes kötődés | `AboutPage` összefoglaló |
| 8 | **Önteszt** → eredmény → **e-mail-gyűjtés + konzultációs CTA** (ÚJ, 2.2) | Lead (aki még nem vásárol) | `FinancialQuiz` bővítve |
| 9 | **Amit nem kínálok** (gyors meggazdagodás, hype, szerencsejáték) | Bizalom – a kitalált vélemények helyett | `AboutPage` notOffer lista |
| 10 | **Mini-GYIK** – 5 eladási kérdés (2.4) | Kifogáskezelés | új |
| 11 | **Záró CTA** – egyetlen kártya | Cselekvés | a `CtaSection` letisztítva |

A kalkulátor átkerül a „Csomagok” alá, vagy önálló `/kalkulator` oldalra (SEO-értékes, és hirdetésekből is ide lehet terelni).

### 2.2 Lead-gyűjtés (ma teljesen hiányzik)

| Eszköz | Most | Javaslat |
|---|---|---|
| **Pénzügyi önteszt** | Eredményt mutat, utána nincs semmi | Eredmény után: **„Kérd e-mailben a szintedhez tartozó 5 lépéses tervet”** (név + e-mail + hozzájárulás) → automatikus e-mail → 3 napos utókövető sor → konzultációs meghívó |
| **Befektetési kalkulátor** | A CTA a foglalásra visz | Ugyanez: „Elküldöm az eredményt PDF-ben” + e-mail |
| **Hírlevél** | E-mail-infrastruktúra (sor, leiratkozás) kész, feliratkozás nincs | Feliratkozó doboz a láblécben, a GYIK alján és a trade-napló alatt: **„Heti 5 perces piaci összefoglaló – a saját trade-jeimmel”** |
| **Lead-mágnes (új)** | – | „**TBSZ, ETF, vésztartalék – kezdő befektetői ellenőrzőlista**” (PDF), a GYIK tartalmából |

Adatbázis: új `leads` tábla a Supabase-ben (név, e-mail, forrás, kvízpont, hozzájárulás, időbélyeg), opcionálisan Airtable-szinkronnal (az integráció már megvan).

### 2.3 Bizalomépítés – mire cserélném a kitalált elemeket
- **Törlendő:** a 3 kitalált ügyfélvélemény (`Trust.tsx`, „Marcus”…), és az igazolatlan „Tanúsított tanácsadó (folyamatban)” kitétel, amíg nincs mögötte konkrétum.
- **Helyette, most:**
  - „**Hogyan vezetem a naplót?**” módszertani doboz: minden lezárt trade bekerül, veszteség is; dátum, belépő, kilépő; a hozam pozícióméret nélkül számolódik.
  - **Valódi LinkedIn-link** (most az általános `linkedin.com` van benne).
  - **Impresszum** a láblécben (név, elérhetőség, adószám az indulás után).
- **Később:** valódi vélemények az első fizetős ügyfelektől, írásos hozzájárulással, keresztnévvel, korral és foglalkozással.

### 2.4 Mini-GYIK az értékesítéshez (a főoldalon, a záró CTA előtt)
1. Mennyibe kerül? → link a csomagokhoz
2. Mi történik az ingyenes konzultáción? Kell-e utána bármit vásárolnom?
3. Megmondod, mibe fektessek? → őszinte válasz: oktatás és rendszer, nem konkrét termékajánlás
4. Kezdőként is érdemes? Mennyi pénz kell hozzá?
5. Miben különbözöl egy banki tanácsadótól vagy egy tőzsdei jelzéseket árusító csoporttól?

### 2.5 Forgalomterelés és mérés (az oldal technikai oldala)
- **Mérés:** a Lovable beépített analitikája + UTM-paraméterek minden közösségimédia-linken; később Meta/Google pixel **sütihozzájárulással** (ehhez cookie-banner kell, ami most nincs).
- **SEO:** külön `title`/`description` és megosztási kép minden oldalra; a GYIK témáiból blogcikkek (`/blog/tbsz-mi-az`, …).
- **Közösségi média → oldal:** egyedi landing oldal a videókhoz („Ezt a trade-et zártam ma – itt a teljes napló”).

---

## 3. ÉRTÉKESÍTÉSI TERV – értékesítési csatornák az oldalon

### 3.1 Új szekció és oldal: „Csomagok” (`/csomagok`, és röviden a főoldalon)

*(Kezdő projekthez igazított, alacsony belépési árak – 2026. október 3-án frissítve. Online fizetés egyelőre nincs; a csomagok foglalása a konzultáción vagy e-mailben történik.)*

| Kártya | Ár | Fő elemek | Gomb |
|---|---|---|---|
| **Ingyenes konzultáció** | 0 Ft | 30 perc · online · kötelezettség nélkül | Időpontot foglalok |
| **Stratégiai óra** | 7 900 Ft | 60 perc · egy konkrét kérdés (TBSZ, ETF, vésztartalék) · írásos összefoglaló | Érdekel → konzultáció |
| **„Alapoktól a rendszerig”** – *Legnépszerűbb* jelvénnyel | 24 900 Ft | 4 × 60 perc 1:1 · személyre szabott tanulási terv · 30 nap e-mailes támogatás · **elégedettségi garancia az 1. alkalom után** | Ezt választom |
| **Portfólió-átvilágítás** | 12 900 Ft | Költség-, diverzifikációs és kockázati elemzés · írásban · oktatási jelleggel | Érdekel → konzultáció |
| **Elemzői közösség** – *Alapító tagság* jelvénnyel | **az első hónap ingyenes**, utána 2 990 Ft/hó (alapító tagi ár, amíg tag maradsz; később 4 990 Ft/hó) | Heti összefoglaló · élő trade-napló · havi élő Q&A | **Csatlakozom alapító tagként** |

A kártyák alatt: valós szűkösség („Havonta max. 5 új 1:1 ügyfél”), kockázati figyelmeztetés, és egy link: „Nem tudod, melyik kell? → Ingyenes konzultáció”.

### 3.2 Foglalási folyamat (`/booking`) – értékesítési szempontú javítások
1. **Dupla foglalás tiltása:** a már lefoglalt idősávok ne legyenek választhatók. Ez most hiányzik.
2. **Előzetes kérdőív** a foglaláskor: cél, időtáv, megtakarítás nagyságrendje (sávosan), mit próbált eddig. Így a 30 perc értékesítési szempontból is hatékonyabb.
3. **Naptármeghívó** (.ics) és **emlékeztető e-mail** 24 órával és 1 órával a hívás előtt (a sablonrendszer kész, bővíteni kell).
4. **Köszönőoldal** a foglalás után, következő lépéssel: „Amíg vársz: töltsd ki az öntesztet / nézd meg a naplót”.
5. Az oldal felső részén egy sor: **„Mi történik a hívás után?”** – nincs kötelező vásárlás; ha tudok segíteni, írásban küldök ajánlatot.

### 3.3 Online fizetés és rendelés – ⏸ KÉSŐBB (a tulajdonos döntése szerint, az oldal publikálása után)
- **Stripe** vagy **Barion** fizetés a csomagkártyákról (Barion a magyar piacon ismertebb, Stripe könnyebb előfizetésre).
- Pénznem **USD → HUF** (a rendelési funkció alapértelmezése most USD).
- **Automatikus számla** (Számlázz.hu / Billingo integráció), rendelés-visszaigazoló e-mail (a sablon kész).
- ÁSZF elfogadása kötelező jelölőnégyzettel a fizetés előtt.

### 3.4 Navigáció és CTA-egységesítés (`Navbar.tsx`)
| | Most | Javaslat |
|---|---|---|
| Menüpontok | Rólam · Folyamat · Foglalás · GYIK | **Csomagok** · Trade-napló · Rólam · GYIK |
| Fejléc-gomb | „Időpontfoglalás” | „**Ingyenes konzultáció**” |
| Mobilon | Teljes képernyős menü | + **ragadós alsó sáv** egyetlen gombbal: „Ingyenes konzultáció” |
| Trade-napló | Nincs önálló oldal (a teljes `TradeResults` lista sehol nem jelenik meg) | Önálló **`/eredmenyek`** oldal a teljes listával és a módszertannal |

### 3.5 Csevegő („Talk to AI” / „Segíthetek?”)
Értékesítési szerep: az árakra, a folyamatra és a „mit kapok” kérdésekre válaszoljon, és tereljen a konzultációra. Ne adjon konkrét befektetési ajánlást – ezt a botnak írt utasításba bele kell foglalni.

---

## 4. Mérőszámok (KPI) – ebből látjuk, hogy működik-e

| Lépés | Mérőszám | Első 3 hónap célja |
|---|---|---|
| Látogató → lead | önteszt/kalkulátor/hírlevél feliratkozás | ≥ 8% |
| Lead → konzultáció | foglalások / leadek | ≥ 5% |
| Konzultáció → vásárlás | fizetős csomag / megtartott konzultáció | ≥ 25% |
| Hírlevél | megnyitás / kattintás | ≥ 40% / ≥ 5% |
| Alapító tagok | csatlakozott közösségi tagok | ≥ 20 fő |

---

## 5. Megvalósítási sorrend (javaslat)

| Fázis | Tartalom | Miért ez a sorrend |
|---|---|---|
| **1. Tisztítás** | Kitalált vélemények és hamis sürgetés ki, trade-statisztika javítása, „szignál” → „jelzés” (vagy törlés), LinkedIn/e-mail javítása | Jogi és bizalmi kockázat – ezt kell elsőként rendezni |
| **2. Pozicionálás** | Hero új szövege, egységes CTA, navigáció | Kis munka, nagy hatás |
| **3. Lead-gyűjtés** | `leads` tábla, önteszt/kalkulátor e-mail-gyűjtés, hírlevél-feliratkozás | Ettől kezd épülni a lista |
| **4. Ajánlat** | `/csomagok` oldal és főoldali szekció, alapító tagság a közösséghez | Árazás az oldalon |
| **5. Értékesítési folyamat** | Foglalási javítások, emlékeztetők (a fizetés és a számlázás később) | A fizetésről a tulajdonos később dönt |
| **6. Főoldal-átrendezés** | Új szekciósorrend, mini-GYIK, `/eredmenyek` oldal | Ha a részek megvannak, összerakjuk |

---

## 6. Kész Lovable-utasítások (jóváhagyás után küldöm)

*A projekt Knowledge-beállítása CARE-keretet kér (Context, Action, Result, Example), ezért abban a formában írtam őket. Minden utasítás egy fázis, így egyenként ellenőrizhetők, és a Lovable-kreditet is fázisonként használják.*

**1. fázis – Tisztítás**
> **Context:** A Rajmi Investments oldal bizalmi és jogi szempontból kockázatos elemeket tartalmaz.
> **Action:** (1) Töröld a `Trust.tsx` három kitalált ügyfélvéleményét és a „Tanúsított tanácsadó (folyamatban)” elemet. (2) A `Hero.tsx`-ből töröld a `GridCtaOverlay` komponenst és a „Cselekedj még ma!” feliratot. (3) A `HeroTerminal.tsx`-ben a 130/56% fix értékek helyett a `trades` listából számolj, a „LIVE” feliratot cseréld erre: „Trade-napló · frissítve: <utolsó trade dátuma>”. (4) A láblécben a LinkedIn-link legyen paraméterezhető, az e-mail-domaint egységesítsd.
> **Result:** Az oldalon csak valós, ellenőrizhető állítások maradnak.
> **Example:** Az összesítő dobozban 101 lezárt trade, 55% nyerési arány, +3,40% átlag/trade – a listából számolva.

**2. fázis – Pozicionálás**
> **Context:** Az oldal fő célcsoportja a 20–35 éves, bizonytalan megtakarító; a pozicionálás: „átlátható befektetési mentor”.
> **Action:** A `HeroTerminal.tsx` főcíme legyen „Befektetés rendszerrel – nem megérzésből.”, az alcím „Független, jutalékmentes mentorálás, hogy a megtakarításod ne az inflációt finanszírozza.”, a USP-sor „Minden trade-emet nyilvánosan vezetem – a veszteségeseket is.” Az elsődleges gomb „Ingyenes 30 perces konzultáció →” (/booking), a másodlagos „Hol tartok most? – 2 perces önteszt” (főoldali kvízhez görget). A gombok alá kerüljön egy háromelemes bizalmi sáv. A navigációs gomb felirata „Ingyenes konzultáció”; mobilon legyen ragadós alsó CTA-sáv.
> **Result:** Egységes üzenet és egy fő CTA az egész oldalon, a jelenlegi dark terminal arculat megtartásával.
> **Example:** Lásd a tervezet 1.2-es táblázatát.

**3–6. fázis** – a fenti minta szerint, a tervezet 2.2, 3.1–3.4 és 2.1 pontjai alapján. A jóváhagyott 1–2. fázis után írom meg őket véglegesre, hogy a közben hozott döntéseidet (árak, közösségi platform) beépíthessem.

---

## 7. Döntések, amelyek tőled kellenek

1. ~~Árak~~ – döntés: **alacsonyabb, kezdő projekthez illő árak** (3.1).
2. ~~Fizetés~~ – később (a tulajdonos jelez).
3. ~~Közösség várólistával~~ – döntés: **nincs várólista**, alapító tagokat toborzunk most.
4. ~~„Szignál” szó~~ – döntés: **„jelzés”**, vagy törlés, ahol nem illik.
5. ~~Sorrend~~ – döntés: az 1–2. fázis elindítva (2026. október 3.).
