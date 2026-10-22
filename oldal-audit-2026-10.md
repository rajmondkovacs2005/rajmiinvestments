# Rajmi Investments – teljes oldalaudit

*2026. október 22. · A Lovable-projekt aktuális kódja alapján (utolsó módosítás: 2026.10.18.)*
*Szempontrendszer: a könyv „Hogyan fest egy profi reklámszöveg?” fejezete – meggyőző sztori, egyediség, érzékeny pontok, anyagi érvek, hitelesség, egyszeri alkalom, hozzáértés bizonyítása, jó stílus és izgalmas cím, tömörség.*

> **Röviden:** az oldal *kinézete* sokat fejlődött, és a főcím erős. A legnagyobb gondok a *tartalomban* vannak:
> 1. **az oldal ellentmond a saját fő ígéretének** („a veszteségekkel együtt”, de csak nyertes trade-eket mutat);
> 2. **a kalkulátor irreális hozamokat ígér, és befektetési tanácsnak minősülhet**;
> 3. **a főoldal túl hosszú, és túl sok rajta a félelemkeltés**, miközben az ajánlat, a történeted és a bizonyíték alig látszik;
> 4. **hiányoznak a kötelező jogi oldalak**, pedig az oldal személyes adatot gyűjt.
>
> Ezeket publikálás előtt mindenképp rendezni kell.

---

## 1. Kritikus hibák – publikálás előtt javítandók

| # | Hiba | Hol | Miért súlyos |
|---|---|---|---|
| K1 | **A „Valós eredmények” rész csak 8 nyertes trade-et mutat** (FSLR +56%, ASTS +45%…), egyetlen veszteséget sem. | Főoldal, a hero alatt | A hero azt ígéri: *„Nyilvános trade-napló – a veszteségekkel együtt.”* Aki görget, az ellenkezőjét látja. Ez a márka legfontosabb ígéretét teszi hiteltelenné. A teljes, 101 tételes napló (benne a veszteségekkel) **sehol nem érhető el az oldalon**. |
| K2 | **A kalkulátor hozamai irreálisak.** „Növekedésorientált” profil: *pesszimista* évi 11%, reális 17,5%, optimista 22%. | Főoldal, legalul | A „pesszimista” forgatókönyvben sincs veszteség, pedig egy 20% kriptót tartalmazó portfólió egy rossz évben akár 30–50%-ot is eshet. Ez félrevezető hozamígéret. Pont az, amit az oldal máshol elítél („nincsenek garantált hozamok”). |
| K3 | **A kalkulátor „személyre szabott portfóliót” ad konkrét arányokkal** (pl. 20% kripto, 40% növekedési részvény), és azt írja: *„megmutatjuk, hogyan kezdheted el pontosan ezt a portfóliót felépíteni”*. | Főoldal, kalkulátor 3–4. lépés | Személyre szabott befektetési ajánlásnak minősülhet. Ehhez Magyarországon engedély kell (Bszt.), a kriptónál MiCA-engedély. Az oldal többi része épp ezt kerüli („befektetési tanácsot nem ad”). |
| K4 | **Hiányzik az impresszum, az adatkezelési tájékoztató és az ÁSZF.** | Egész oldal | A foglaláskor nevet és e-mail-címet gyűjtesz, a Voiceflow-chat külső szolgáltató, és később fizetés is lesz. Ezek nélkül az oldal nem élesíthető (GDPR, elektronikus kereskedelmi törvény). |
| K5 | **A „Mielőtt tovább görgetsz” blokk forrásai valószínűleg pontatlanok:** „90% – ESMA 2024”, „70% – ESMA leverage study”, a 6,5%-os kártya szövege. | Főoldal, piros blokk | Ezt már jeleztem, de nem lett javítva. Egy pénzügyi oldalon egy hamis forrás az egész oldal hitelességét rombolja. |
| K6 | **A Segítség oldal egy nem létező űrlapra küld.** A GYIK azt írja: „jelezd lent a problémabejelentőben”, a chat felett az áll, hogy „azonnal válaszolok”, de bejelentő űrlap nincs. A chatbot utasítása szerint ő sem tud bejelentést küldeni. | /segitseg | Akinek valódi problémája van (pl. lemondaná az időpontot), zsákutcába jut. Az 5/5-ös prompt (űrlap + mentés + e-mail) még nem futott le. |
| K7 | **Üres helykitöltők a Rólam oldalon:** egy üres keretes címke és két üres bekezdés közvetlenül a fotód mellett. | /about | Látható, üres keret és lyuk, épp ott, ahol a bemutatkozó szövegednek kellene lennie. |
| K8 | **A fotód alternatív szövege: „független pénzügyi tanácsadó”.** | /about | Ugyanaz a jogi gond, mint K3-nál, és ellentmond a lábléc „nem minősül pénzügyi tanácsadásnak” mondatának. |

---

## 2. Értékelés a könyv szempontjai szerint

### 2.1 Meggyőző sztori – ⚠️ van, de el van rejtve
- **Erősség:** a történeted („Szerencsejátékosból tudatos befektető” – 2024-ben stratégia nélkül veszítettél, tanultál, ma rendszerrel dolgozol) **a legjobb tartalmi eszközöd**. Hiteles, és pont a célcsoport félelmére felel („én is elbuknék”).
- **Gond:** csak a Rólam oldal közepén van, egy kártyás idővonalon, apró, 13 px-es betűkkel. **A főoldalon egyetlen mondat sincs belőle.** A könyv szerint a sztori az egyik legerősebb eladási elem, nálad mégis a legkevésbé látható.
- **Ügyfélsztori** (a könyv „aki a szolgáltatásunkkal oldott meg egy problémát” példája) még nem lehet, mert nincs ügyfél. Ezt jól kezeled azzal, hogy nincs kitalált vélemény. Az első ügyfelektől viszont **tudatosan gyűjts** írásos véleményt, hozzájárulással.

### 2.2 Egyediség, különlegesség – ⚠️ jó ötlet, rossz megvalósítás
- **Az egyediséged:** fiatal, saját bukásából tanult mentor, aki **nyilvánosan vezeti a trade-jeit, a veszteségeket is**, nem árul terméket, és a kezdők nyelvén beszél. Ez a magyar piacon valóban ritka.
- **Gond:** lásd K1. Az oldal *mondja*, de nem *mutatja*. Ráadásul:
  - a napló **3 hónapja nem frissült** (utolsó trade: 2026.07.24.). A „frissítve” felirat így inaktivitást sugall;
  - a „Valós eredmények” szűrőjében az „Utolsó 30 nap” és az „Utolsó 90 nap” **üres listát ad** („Nincs a szűrésnek megfelelő trade”);
  - a 101 tétel között 8 dátum nélküli, mind nyereséges BTC/MSTR trade van, és két tételnél valószínű elírás a dátumban (2025.05.15, 2025.05.29). Ezek javítják a statisztikát, ezért gyanúsak.
- **A szolgáltatásod maga sehol nem jelenik meg a főoldalon.** Nincs „mit kapsz” vagy „kinek szól” rész. Az ajánlat és az ár csak a Folyamat oldal alján látszik.

### 2.3 Érzékeny pontok – ⚠️ túlzásba vitt félelemkeltés, a valódi félelmek kimaradnak
- A főoldalon **három egymást követő félelemblokk** van: „Aggódsz…?” oszlopdiagram → „Mielőtt tovább görgetsz… 30 másodperc több pénzedbe kerülhet” → infláció. Egy kezdő ennyi riogatás után inkább elmegy, mint hogy foglaljon.
- **A célcsoport valódi félelmei kimaradnak:** „nem értek hozzá”, „félek, hogy elveszítem a pénzem”, „nem tudom, kiben bízhatok”, „nincs rá időm”, „kevés a pénzem ehhez”. Ezekre egyetlen szekció sem felel közvetlenül.
- A piros „sokkoló” blokk **traderekről és tőkeáttételről** szól, nem kezdő megtakarítókról. Nem a célcsoportodat szólítja meg.
- A „görgess lejjebb a megoldásért!” gomb **megoldást ígér, de lejjebb újabb ijesztő adatok jönnek**. Ez megtöri a bizalmat.
- A megtakarítási oszlopdiagramon **nincsenek számok, időtáv és forrás**. Csak hangulatot kelt, és egy figyelmes olvasó észreveszi.

### 2.4 Anyagi jellegű érvek – ⚠️ van szám, de rossz helyen és rosszul
- **Jó:** az inflációs kártyák most pontos, friss adatokat mutatnak (17,6%, −35%, 86%).
- **Rossz:** a kalkulátor (K2, K3) túl szép számokat mutat, és ez ellenük dolgozik.
- **Hiányzik:** nincs összevetve, **mennyibe kerül a szolgáltatás ahhoz képest, amit megspórol**. Egy őszinte példa a könyv szellemében: *„Egy átlagos befektetési alap évi kb. 1,5–2% kezelési költsége 5 millió forintnál évi 75–100 ezer Ft – minden évben. A mentorcsomag egyszeri 24 900 Ft.”* A pontos költségszintet élesítés előtt ellenőrizni kell.

### 2.5 Hitelesség – ❌ a leggyengébb pont
- Kitalált vélemények már nincsenek (jó), de **semmi sincs a helyükön**.
- Nincs valódi LinkedIn-link (rejtve), **az e-mail-domain hibás lehet** (`info@rajminvestments.com`, egy „i” hiányzik a márkanévhez képest), nincs impresszum, és nincs teljes, ellenőrizhető napló.
- **Négy különböző kockázati figyelmeztetés** van az oldalon: alsó sáv, nagy piros csík a trade-ek előtt, lábléc, Trust-blokk. A piros csík közvetlenül a hero után **elsőként „⚠ Figyelmeztetés”-t mutat** a bizonyíték helyett. Ez kötelező, de rossz helyen és túl hangos.

### 2.6 „Soha vissza nem térő alkalom” – ✅ helyesen óvatos, de nincs valódi ajánlat
- A hamis sürgetést kivettük (jó). A „Havonta max. 5 új ügyfél” is eltűnt a heróból. Ha ez nem igaz, ez is helyes.
- **Viszont nincs egyetlen valódi, időhöz kötött ajánlat sem.** A korábban megbeszélt **alapító tagság** (első hónap ingyen, utána 2 990 Ft/hó) **nincs az oldalon**. Egy őszinte, valós határidő vagy keret (pl. „Az első 10 ügyfélnek a csomag 19 900 Ft, 2026. december 31-ig”) jogszerű és hatásos, de csak akkor, ha valóban tartod.

### 2.7 Hozzáértés bizonyítása – ❌ gyenge
- Képesítés, végzettség vagy tanúsítvány nincs feltüntetve. A Rólam oldal statisztikái gyengék vagy semmitmondók: „2024 – első befektetés”, „2+ év aktív tanulás”, **„100% adatalapú döntés”** (ez utóbbi ellenőrizhetetlen, és inkább hiteltelenít).
- A trade-statisztika **trade-enkénti átlaghozamot** mutat (+3,40%) pozícióméret nélkül. Ez nem mondja meg, mennyit nőtt a tényleges tőkéd. Egy tapasztalt olvasó ezt észreveszi.
- **Amivel valóban bizonyíthatnád:** a teljes napló, egy portfólió-szintű tőkegörbe (anonimizált brókerkimutatásból), és rövid, érthető magyarázó tartalmak (a befektetési GYIK jó alap). Ha tanfolyamot vagy vizsgát végeztél, nevezd meg pontosan.

### 2.8 Jó stílus, izgalmas cím – ✅ / ⚠️
- **Jó:** „Befektetés rendszerrel, nem megérzésből.”, „Szerencsejátékosból tudatos befektető”, „A többség veszít. Te dönthetsz másképp.”
- **Gyenge:**
  - „görgess lejjebb a megoldásért!” (kisbetűs, ígéretet szeg);
  - „Mielőtt tovább görgetsz” (bulvár);
  - „Aggódsz, hogy megtakarításaid elveszíthetik értéküket?” (vékony betű, nem illik a többihez).
- **Elírás:** Rólam oldal: *„segítek neked elkerülni **ezelet**”* → **ezeket**.
- **Megszólítás:** a kalkulátor és a Rólam oldal „**mi**” formában beszél („megmutatjuk”, „visszajelzünk”), az oldal többi része „**én**” formában. Egyszemélyes vállalkozásnál az „én” a hitelesebb.
- **Ellentmondó válaszidő:** a kalkulátor „48 órán belül” visszajelzést ír, a foglalás és a GYIK „24 órán belül”-t.

### 2.9 Tömörség – ❌ a főoldal túl hosszú és túl lassú
- A főoldal sorrendje: hero → piros figyelmeztetés → 8 nyertes trade → CTA-doboz → „Aggódsz?” oszlopdiagram → „Mielőtt tovább görgetsz” (3 gépelt kártya + nyíl + konklúzió) → infláció (3 kártya + nyíl + konklúzió) → **8 kérdéses önteszt** → **4 lépéses kalkulátor, benne újabb 5 kérdés**.
- **Két kérdőív egymás után** (8 + 5 kérdés). Senki nem tölti ki mindkettőt.
- **Az animációk visszatartják a tartalmat:** a piros blokkban a kártyák szövege betűnként gépelődik, és a „Te dönthetsz másképp.” csak kb. 4 mp, a gomb kb. 6 mp után jelenik meg. Az infláció blokkban a cím alatti sor 2,5 mp-ig várat, a gomb a kártyák után még kb. 5 mp-et. Aki gyorsan görget, **üres területeket lát**.
- **Az önteszt zsákutca:** az eredmény után nincs következő lépés, se gomb, se e-mail-gyűjtés.

---

## 3. Kinézet és egységesség

| Terület | Gond | Javaslat |
|---|---|---|
| Betűtípusok | 4 család: Inter, Playfair, JetBrains Mono, és a GYIK oldalon **Fraunces**. | 2 stílus, ahogy a heróban: Playfair a címekhez, JetBrains Mono a többihez. Az Inter csak a hosszabb folyószövegekhez maradjon. |
| Színek | A **Foglalás oldal saját zöld palettát** használ (#1fc98a, #0b0f0e), a **GYIK aranyat**, a kalkulátor zöld színátmeneteket, a hero alatti CTA-doboz zöld körvonalas gombot. | Egy paletta: kék elsődleges gomb, zöld = pozitív, piros = veszteség, borostyán = infláció. A Foglalás és a GYIK oldalt hozzá kell igazítani. |
| Gombok | 6-féle felirat és 4-féle stílus: „Ingyenes konzultáció”, „Időpont foglalása”, „Időpontfoglalás”, „Foglalok ingyenes konzultációt”, „Megvédem a tőkémet”, „Időpontot választok”. | Egy stílus (kék vagy a hero színátmenete), a felirat legfeljebb 2-féle. |
| Emojik | A Rólam idővonalán 🎒⚠️📚💡🎯, a hero alatti CTA-dobozban ✅🕐💻, a kalkulátorban 📊. | A terminál-stílusban zavaróak és olcsó hatásúak. Cseréld egyszerű ikonokra vagy jelekre (▸, ✓). |
| Foglalás oldal | Más színvilág, nincs adatkezelési hozzájárulás, és **a már lefoglalt időpontok nem tűnnek el** (dupla foglalás lehetséges). | A márkához igazítani, hozzájárulást beépíteni, a foglalt időpontokat kizárni. |
| Mobil | A főoldalon a fix alsó CTA-sáv, a Voiceflow-buborék és a kockázati sáv egyszerre is versenyezhet a helyért. | Telefonon végig kell nézni. Innen az előnézetet nem tudom megnyitni (lásd 6. pont). |

---

## 4. Javasolt új főoldal-szerkezet

A könyv logikája szerint: **figyelem → érzékeny pont és sztori → egyediség és bizonyíték → megoldás és anyagi érv → hitelesség → cselekvés.**

| # | Szekció | Mi van benne | Mi lesz a mostaniból |
|---|---|---|---|
| 1 | **Hero** | Marad, ahogy van. | – |
| 2 | **„Ismerős?” + a te történeted** | 3–4 valódi félelem röviden („Nem értek hozzá.” „Féltem a pénzem.” „Nem tudom, kiben bízzak.”), mellette fotó és 3 mondat a történetedből, link a Rólam oldalra. | **Új.** A Rólam oldal tartalmát hozza előre. |
| 3 | **Nyilvános trade-napló** | Az **utolsó 8 trade dátum szerint, a veszteségekkel együtt**, összesítő (pontos számokkal), módszertani megjegyzés, link a **teljes naplóra** (új `/eredmenyek` oldal), és alatta kicsi, szürke kockázati sor. | A mostani „csak nyertes” lista helyett. A nagy piros csík megszűnik. |
| 4 | **Miért fontos ez? (infláció)** | A borostyán inflációs blokk, rövidebb animációval. | Megmarad. A „Mielőtt tovább görgetsz” és az „Aggódsz?” blokk **kikerül** (vagy a piros blokk ellenőrzött forrásokkal később blogcikk lesz). |
| 5 | **Mit kapsz és mennyiért** | A 4 lépés 4 ikonnal, ár, egy őszinte költség-összevetés, és **egy valós, határidős ajánlat**, ha vállalsz ilyet. | A Folyamat oldal ajánlatpaneljének rövid változata. |
| 6 | **Bizalom** | Valódi vélemények, amint lesznek. Addig: „Amit nem kínálok” (gyors meggazdagodás, hype, szerencsejáték) és a pontosan megnevezett képesítésed vagy tanulmányaid. | A Rólam oldalról. |
| 7 | **Önteszt** | **Egy** kérdőív (a mostani 8 kérdéses), az eredmény után konkrét következő lépéssel (konzultáció és/vagy e-mail-feliratkozás). | A kalkulátor **kikerül** (vagy egy őszinte, csak inflációt vs. megtakarítást számoló egyszerű kalkulátor lesz belőle, portfólió és hozamígéret nélkül). |
| 8 | **Mini-GYIK + záró CTA** | 4–5 kérdés: Mennyibe kerül? Mi történik a konzultáción? Megmondod, mibe fektessek? Kezdőként is érdemes? | Új, a meglévő GYIK-ből. |

Ezzel a főoldal kb. **a felére rövidül**, és minden szekciónak egy dolga van.

---

## 5. Prioritási sorrend

**P0 – publikálás előtt kötelező**
1. K1: a trade-bemutató mutassa a veszteségeket is, és legyen elérhető a teljes napló.
2. K2 és K3: a kalkulátor kivétele, vagy átírása portfólió és irreális hozam nélkül.
3. K4: impresszum, adatkezelési tájékoztató, ÁSZF, és hozzájárulás a foglalási űrlapon.
4. K5: a piros blokk eltávolítása vagy a források javítása.
5. K6: a bejelentő űrlap (5/5-ös prompt) beadása, vagy a szövegek átírása, hogy ne ígérjenek nem létező űrlapot.
6. K7 és K8: az üres helyek kitöltése a Rólam oldalon, és az alternatív szöveg javítása.
7. Az e-mail-domain ellenőrzése, a foglalt időpontok kizárása, az elírás javítása.

**P1 – a meggyőzőerőhöz**
8. Az új főoldal-szerkezet (4. pont), benne a sztori és az ajánlat a főoldalon.
9. A trade-napló frissítése, és rendszeres (pl. heti) frissítés vállalása.
10. Egy valós, határidős ajánlat (ha vállalod), és vélemények gyűjtése az első ügyfelektől.

**P2 – csiszolás**
11. Egységes betűk, színek és gombok (Foglalás és GYIK oldal).
12. Az emojik cseréje, és az animációk gyorsítása (a tartalom 1 mp-en belül látsszon).
13. Az „én” forma mindenhol, és egységes válaszidő (24 óra).

---

## 6. Ahol elakadtam, vagy tőled kell információ

1. **Az élő előnézetet nem tudom megnyitni** ebből a környezetből, csak kódot és a főoldal képernyőképét látom. A mobilos kinézetet és az animációk tényleges érzetét **neked kell telefonon végignézned**.
2. **Valódi adatok kellenek tőled**, ezeket nem tudom és nem is szabad kitalálnom:
   - a helyes e-mail-cím és a LinkedIn-profil;
   - van-e bármilyen képesítésed, tanfolyamod, vizsgád (pontos név, intézmény, év);
   - a 8 dátum nélküli BTC/MSTR trade dátuma, és a két 2025-ös dátum helyessége;
   - frissebb trade-ek július óta;
   - az ár (24 900 Ft) végleges-e, és vállalsz-e határidős vagy keretes ajánlatot;
   - igaz-e a „havonta legfeljebb 5 új ügyfél”.
3. **A jogi oldalak szövegét** (impresszum, adatkezelés, ÁSZF) sablonból elő tudom készíteni, de **élesítés előtt jogásznak kell átnéznie**, különösen a Bszt./MiCA-szempontok miatt.
4. **A chatbot most működik-e:** a háttérfüggvény és a válaszkönyv-tábla már a kódban van. Hogy a táblában vannak-e sorok, és a chat élesben válaszol-e, azt adatbázis-lekérdezéssel ellenőrizni tudom, ha kéred.
