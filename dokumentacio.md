# Projekt feladat: Weboldal készítés
## Ismertető
### Készítő
Fóti Kristóf
### Feladat leírás
Feladatom, hogy egy általam válaszott témában egy komplett weboldalt hozzak létre, amely megfelel valamennyi kritériumnak.
### Ötlet
A weboldalamon a cs2-ben található **armorypass** befektetési megtérülését fogom kíszámítani, a különböző lehetőségekkel. Az **armorypass** egy olyan befektetési mód, amivel ha az ember okosan csinálja, alacsony kocgázattal lehet mérsékelt mennyiségű pénzt keresni. Egy **armorypass** 14 euró, ezzel 40 csillagot kap az ember, amit a játék játszásával tud kiváltani. Ezeket a csillagokat a shopban lehet elkölteni, ebből olyan játékbeli tárgyakat lehet venni, amit később értékesíteni lehet pénzért. Különböző ritkaságú tárgyak többet-kevesebb érnek, így valamennyi a szerencsén is múlik, hogy mennyit kap vissza az ember, ezért érdemes kiszámítani, hogy mit éri meg a legjobban kiváltani. Ahhoz, hogy ezt kiszámítsul tudnunk kell mik a tárgyak, mennyi csillagba kerül, mennyiért lehet eladni, valamint mennyi esély van, hogy azt kapjuk. Az információk segítségével ki lehet számítani 1-1 kollekciónak mi az átlagos megtérülése.
### Funkciók
- Megtérülési ráta százalékban, valamint pénzben kifejezve is.
- Random generált szimuláció a nyitásokra.
- A különböző kollekciók ismertetése.
## Megvalósítási terv
### Fejlesztői környezet
A fejlesztés Visual Studio Code-ban, a verziókezelés githubon fog történni.
A kód három alapvető külön részben lesz elkeszítve
1. HTML - maga az oldal 
2. CSS  - az oldal kinézete
3. JS   - az oldal szíve, függvények, számításokkal
Ezeken felül a képek egy képek mappán belül, azon belül különböző kollekciókra lesznek lebontva.
### Script
A különböző kollekciók 1-1 tömböt fognak alkotni, amelyekben struktúraként minden egyes tárgy szerepelni fog az alábbi adatokkal
- Neve
- Mennyi csillagba kerül
- Mekkora esély van, hogy az kapjuk
- Mennyi a piaci értéke

Mivel valósidejű piaci értékhez különböző API-ok szükségesek, ezért a feladat elkészítése során, az éppen aktuális értéküket fogja mindegyik tárgy megkapni statikusan.
Alapvető elv, hogy nem ismételünk egy kódban, ezért az összes számítást ami a megtérülés, avagy bármit számol függvényekben fogok megoldani, amit mindenre lehet használni.
### Stílus - Felépítés
Egyszerú letisztult stílust fogok használni, az oldal konténerek és dobozok segítségével lesz felépítve.
Mivel a feladat kritéruma, ezért három oldal lesz.
1. Főoldal - az armory alapvető lényegét ismerteti a különböző kollekciók láthatóak itt megtérülésükkel.
2. Kollekciók - Script segítségével meglehet nézni a kollekciókban lévő tárgyakat, valamint azoknak árát, és ritkaságát.
3. Szimulációs oldal - Script segítségével az összes kollekciót le lehet szimulálni, mit kapnánk ha azt élesben nyitnánk, valamint a különböző ehhez tartozó adatokat.