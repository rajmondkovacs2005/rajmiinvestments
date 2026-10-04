# Konklúzió-panel átalakítása – „három adat, egy nyíl”

*Rajmi Investments · `src/components/site/ShockDataSection.tsx` · 2026. október 4.*
*Fájlok ebben a mappában: `prototipus.html` (böngészőben megnyitható, újrajátszható animáció), `kepernyokep-asztali.png`, `kepernyokep-mobil.png`, `kepernyokep-animacio-kozben.png`.*

> **Státusz: TERVEZET** – a Lovable-projekthez még nem nyúltam.

---

## 1. Mi a gond a mostani blokkal (szerkezeti elemzés)

| # | Megfigyelés a kódban | Következmény |
|---|---|---|
| 1 | A kártyák alatt **három különálló** piros nyíl van (`ConnectorPath` → 3 × `ArrowConnector`), mindegyik a saját kártyája alól mutat le. | Három párhuzamos irány → a szem nem kap egyetlen „tehát”-ot. Az adatok nem *összegződnek*, csak egymás mellett állnak. |
| 2 | A panelen belül a számsor (90% / 6,5% / 70%) és „A többség veszít.” között csak egy vékony vízszintes vonal és a „*Amíg ezt olvasod, valaki más már lépett.*” mondat áll. | A sürgető mondat **épp a bizonyíték és a következtetés közé ékelődik**, és elvágja a logikai láncot. Hangnemben is ütközik a 2. fázisban beállított „nyugodt, rendszerszerű” pozicionálással. |
| 3 | A „A többség veszít.” 3,3 mp, a „Te dönthetsz másképp.” 5,3 mp, a gomb 6,1 mp késleltetéssel jelenik meg. | Görgetés közben a látogató gyakran már továbblép, mire a konklúzió megjelenik. |
| 4 | A gomb felirata „Lépj be most — foglalj konzultációt”. | Eltér a 2. fázisban egységesített „Ingyenes konzultáció” CTA-tól. |

## 2. A javasolt megoldás

```
┌─ piros felső él ─────────────────────────────────────────┐
│     90%              6,5%              70%                │  ← recap sor (marad)
│   ELVESZÍT        ALULTELJESÍT    TŐKEÁTTÉT LIKVIDÁCIÓ    │
│     │                 │                 │                 │  ← 3 szár
│     ╰────────╮        │        ╭────────╯                 │  ← lágy ívek
│              ╰────────┼────────╯                          │  ← ÖSSZEFUTÁSI PONT
│                       │                                   │  ← közös törzs (erősebb)
│                       ▼                                   │  ← egyetlen nyílhegy
│               A többség veszít.                           │  ← a nyíl CÉLJA
│               ─────────────────                           │  ← piros aláhúzás
│             Te dönthetsz másképp.                         │  ← zöld-kék gradiens
│            [ INGYENES KONZULTÁCIÓ → ]                     │
└───────────────────────────────────────────────────────────┘
```

**Vizuális logika:** három mellékág (a három bizonyíték) egy közös törzsbe fut, és egyetlen nyílhegy mutat a következtetésre. Az oldalsó ágak halványabbak (55% átlátszóság), a törzs és a nyílhegy teljes erősségű – vagyis a vonal **erősödik**, ahogy az adatok összeadódnak.

### Változtatások
1. **Új összefutó nyíl a panelen belül**, a recap sor és a „A többség veszít.” között – ez váltja ki a vékony elválasztó vonalat.
2. **A három különálló nyíl (a kártyák alatt) törlődik.** Két nyílrendszer egymás alatt versenyezne; az „egységes nyíl” csak akkor működik, ha egy van belőle. A panel a kártyák alatt marad, a recap sor vizuálisan visszautal rájuk.
3. **„Amíg ezt olvasod, valaki más már lépett.” törlődik** – a lánc nem szakadhat meg, és ez az 1. fázisban kivezetett hamis sürgetés egyik utolsó maradványa.
4. **„A többség veszít.” alá** egy piros, középről kifutó aláhúzás kerül – a nyíl „becsapódási pontja”.
5. **Gyorsabb ritmus** (lásd 3. pont): a teljes jelenet ~3,7 mp alatt lefut 6,5 mp helyett.
6. **CTA:** „Ingyenes konzultáció →” (egységes felirat), stílus változatlan.

Ami **nem változik**: a három kártya, a count-up és gépelés-animációk, a recap sor kinézete, a panel kerete, a `showConclusion` indítási feltétel, színek, betűtípusok.

## 3. Animációs forgatókönyv (a panel megjelenésétől számítva)

| Idő | Esemény |
|---|---|
| 0,10 / 0,25 / 0,40 s | A recap sor 3 száma felúszik (meglévő animáció, rövidebb késleltetéssel) |
| 0,90 / 1,02 / 1,14 s | A három ág kirajzolódik (0,5 s, `pathLength` 0→1); közben a hozzá tartozó szám egyszer piros fényt kap |
| 1,60 s | A közös törzs kirajzolódik (0,3 s); egy fehér-piros fénypont egyszer lefut rajta |
| 1,90 s | A nyílhegy „leérkezik” (0,25 s, drop-shadow fény) |
| 2,00 s | „A többség veszít.” megjelenik |
| 2,35 s | Piros aláhúzás középről kifut |
| 2,80 s | „Te dönthetsz másképp.” megjelenik |
| 3,30 s | CTA gomb |

`prefers-reduced-motion` esetén minden azonnal, végállapotban jelenik meg; a fénypont kimarad. Nincs végtelen pulzálás.

## 4. Technikai megvalósítás (fontos!)

- A nyíl egy SVG, amelynek **viewBox-a a konténer valós pixelméretéből számolódik** (`ResizeObserver`), és az útvonalak is abból készülnek:
  - oszlopközepek: `W/6`, `W/2`, `5W/6` (a recap sor `grid-cols-3`-ból adódik, mobilon is három oszlop marad, így mobilon is működik);
  - oldalág: `M x 0 V 0.2H C x 0.58H, cx 0.42H, cx 0.7H`;
  - középső ág: `M cx 0 V 0.7H`; törzs: `M cx 0.7H V H`.
- **Nem szabad** `preserveAspectRatio="none"` + `vector-effect: non-scaling-stroke` kombinációt használni: a prototípus első változatában ez széles panelen eltörte a rajzolás-animációt (az oldalsó ágak nem értek be középre). Ezt javítottam, és a képernyőképek már a javított változatot mutatják.
- A nyílhegy külön, nem nyújtott kis SVG (22×14) a törzs alatt, így sosem torzul.
- Magasság: `clamp(64px, 9vw, 96px)`.

## 5. Tartalmi figyelmeztetés – a három szám forrása ⚠️

A design bármilyen számmal működik, de a nyíl most még erősebben épít ezekre a számokra, ezért jelzem: **a kártyák forrásmegjelölései közül kettő valószínűleg nem pontos.** Ezt tudásom szerint írom, élesítés előtt mindenképp ellenőrizd a forrásokat:

| Kártya | Most | Amit tudok | Javaslat |
|---|---|---|---|
| 90% | „A szerencsejátékos befektetők 90%-a elveszíti tőkéje 90%-át 90 napon belül. — ESMA, 2024” | Ez a kereskedői fórumokon terjedő „90-90-90 szabály”; nem ismerek ilyen tartalmú ESMA-kiadványt. Az ESMA ténylegesen közölt adata: a lakossági CFD-számlák **74–89%-a veszteséges** (2018-as termékintervenciós döntés). | Pl. „74–89% – a lakossági CFD-számlák ennyi százaléka veszteséges. — ESMA, 2018” |
| 6,5% | „Az aktív kereskedők évente átlagosan 6,5%-ot veszítenek — miközben a piac nő. — Barber & Odean” | A forrás valódi (*Trading Is Hazardous to Your Wealth*, Journal of Finance, 2000): a legaktívabb háztartások évente kb. **6,5 százalékponttal maradtak el a piactól** – vagyis nem 6,5%-ot veszítettek, hanem ennyivel alulteljesítettek. A recap címke („alulteljesít”) jó, a kártya szövege nem. | „…évente átlagosan 6,5 százalékponttal teljesítenek a piac alatt.” |
| 70% | „Tőkeáttételt használó retail befektetők 70%-a elveszíti a teljes befektetett tőkéjét. — ESMA leverage study” | Nem ismerek ilyen nevű ESMA-tanulmányt; az ESMA-adat a veszteséges számlák arányáról szól, nem a teljes tőke elvesztéséről. | Forrás ellenőrzése, vagy csere egy ellenőrzött adatra. |

Ha a számok változnak, a recap sor és a nyíl automatikusan igazodik (a tömbből olvasnak).

## 6. Kész Lovable-utasítás (jóváhagyás után küldöm)

> **CONTEXT:** A `ShockDataSection.tsx` konklúzió-paneljén a három statisztika és a „A többség veszít.” konklúzió között nincs vizuális kapcsolat, a kártyák alatt pedig három különálló nyíl áll. Cél: egyetlen, egységes nyíl, amelyben a három adat összefut és a konklúzióra mutat.
> **ACTION:**
> 1. Töröld a `ConnectorPath` és `ArrowConnector` komponenst és a használatukat (a kártyák alatti három nyíl).
> 2. A panelen belül a recap sor alatti vízszintes elválasztó vonal helyére tegyél egy új `ConvergingArrow` komponenst: egy `aria-hidden` SVG, magassága `clamp(64px, 9vw, 96px)`, a viewBox és az útvonalak a konténer valós méretéből számolódjanak `ResizeObserver`-rel (NE használj `preserveAspectRatio="none"`-t és `vector-effect`-et). Útvonalak: oszlopközepek `W/6`, `W/2`, `5W/6`; oldalág `M x 0 V 0.2H C x 0.58H, cx 0.42H, cx 0.7H`; középső ág `M cx 0 V 0.7H`; törzs `M cx 0.7H V H`. Szín `var(--term-accent-red)`, vonalvastagság 1,5 (törzs 2), oldalágak 55% átlátszóság. Alatta egy külön 22×14-es nyílhegy (`polyline 2,2 11,12 20,2`, vastagság 2,2, `drop-shadow(0 0 6px rgba(248,113,113,.75))`).
> 3. Animáció `motion.path` + `pathLength` 0→1, a `showConclusion` után: ágak 0,9/1,02/1,14 s (0,5 s), közben a hozzájuk tartozó recap szám egyszer piros text-shadow fényt kap; törzs 1,6 s (0,3 s) egy egyszer lefutó fényponttal; nyílhegy 1,9 s. A recap sor késleltetései: 0,1/0,25/0,4 s.
> 4. Töröld az „Amíg ezt olvasod, valaki más már lépett.” bekezdést.
> 5. „A többség veszít.” 2,0 s-nál jelenjen meg, alatta egy piros, középről kifutó aláhúzással (2,35 s, a szöveg 60%-a széles, `linear-gradient(90deg, transparent, var(--term-accent-red), transparent)`). „Te dönthetsz másképp.” 2,8 s, a CTA 3,3 s.
> 6. A CTA felirata: „Ingyenes konzultáció” + nyíl ikon; stílus marad.
> 7. `prefers-reduced-motion`: minden azonnal végállapotban, fénypont nélkül. Nincs végtelen ismétlődő animáció.
> **RESULT:** A három bizonyíték vizuálisan egy nyílba fut össze, ami a konklúzióra mutat; a teljes jelenet ~3,7 mp alatt lefut.
> **EXAMPLE:** Lásd a mellékelt prototípust: recap sor → három ív egy pontba → törzs → nyílhegy → „A többség veszít.” → „Te dönthetsz másképp.” → [Ingyenes konzultáció →]. Ellenőrizd 1280 px-en és 390 px-en: mindhárom ág pontosan egy pontban találkozzon.
