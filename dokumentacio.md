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
## Megvalósítás
### Fejlesztői környezet
A fejlesztés Visual Studio Code-ban, a verziókezelés githubon fog történni.
A kód három alapvető külön részben lesz elkeszítve
1. HTML5 - maga az oldal 
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
1. Főoldal - a különböző kollekciók láthatóak itt megtérülésükkel.
2. Kollekciók - Script segítségével meglehet nézni a kollekciókban lévő tárgyakat, valamint azoknak árát, és ritkaságát.
3. Szimulációs oldal - Script segítségével az összes kollekciót le lehet szimulálni, mit kapnánk ha azt élesben nyitnánk, valamint a különböző ehhez tartozó adatokat.

### Követelmények teljesítése
1. Az oldal 3 oldalból áll
2. Összesen 13db függvény van, amelyből több is paraméteres például kép elérési utat adó függvény
3. A 13db függvény valamennyi függvénye tartalmazza a követelményeknek megfelelő műveleteket, elágazásokat, tömböket, ciklusokat.
4. Sok programozási tétel szerepel az oldalon ilyen például a keresés, összegzés stb.

### Függvények rövid ismertetése

| Függvény megnevezése | funkció |
| --- | --- |
| kollekcioRendezes() | Kollekciók rendezése megtérülés alapján |
| kepElérésiÚt() | Kép elérési út generálás |
| renderKollekciok() | Kollekciók megjelenítése HTML-ben |
| handleImageError() | Kép hibakezelés |
| betoltKollekciok() | Dropdown feltöltés kollekciókkal |
| megjelenitElemek() | Elemek listázása érték szerint |
| betoltSzimulacioKollekciok() | Szimuláció dropdown feltöltés |
| szimulal() | Szimuláció indítása |
| szimulalKollekcio() | Kollekció szimulálása |
| normalizalEselyek() | Esélyek normalizálása |
| kivalasztElem() | Véletlen elem választás |
| megjelenitSzimulacioEredmenyek() | Szimuláció eredmények megjelenítése |
| torolEredmenyek() | Eredmények törlése |

## Mesterséges inteligencia használat
### Prompt
Készíts egy JavaScript függvényt, amely egy kollekciók tömbjét veszi bemenetül, ahol minden kollekció tartalmaz elemeket értékekkel és esélyekkel. Számítsd ki minden kollekció várható értékét (érték * esély), majd a megtérülés százalékos arányát (várható érték / költség * 100), ahol a költség a csillagok száma * 0.35. Rendezd a kollekciókat megtérülés szerint csökkenő sorrendbe, és add vissza az eredményt.
### Eredmény
```javaScript
function kollekcioRendezes() {
    const kollekcioMegterulesek = Kollekciok.map(kollekcio => {
        const varhatoErtek = kollekcio.elemek.reduce((osszeg, elem) => {
            return osszeg + (elem.érték * elem.esély);
        }, 0);
        const kollekcioKoltseg = kollekcio.elemek[0].csillag * 0.35;
        const megterules = (varhatoErtek / kollekcioKoltseg) * 100;
        const legertékesebbElem = kollekcio.elemek.reduce((legjobb, elem) => {
            return elem.érték > legjobb.érték ? elem : legjobb;
        });
        
        return {
            név: kollekcio.név,
            megterules: megterules,
            varhatoErtek: varhatoErtek,
            koltseg: kollekcioKoltseg,
            legertékesebbElem: legertékesebbElem
        };
    });
    
    return kollekcioMegterulesek.sort((a, b) => b.megterules - a.megterules);
}
```
---
### Prompt
Írj egy JavaScript függvényt, amely kollekció neve és elem neve alapján generálja a kép fájl elérési útját. Cseréld ki a szóközöket aláhúzásjelekre, és formázd a következő minta szerint: "kepek/{kollekcio_nev}/{elem_nev}"
### Eredmény
```javaScript
function kepElérésiÚt(kollekcioNev, elemNev) {
    const formazottKollekcio = kollekcioNev.replace(/ /g, '_');
    const formazottElem = elemNev.replace(/ /g, '_');
    return `kepek/${formazottKollekcio}/${formazottElem}`;
}
```
---
### Prompt
Készíts egy JavaScript függvényt, amely betölti az összes kollekció nevét egy select elembe, de csak azokat a kollekciókat, amelyeknek több mint 1 eleme van. A kollekció nevekben cseréld ki az aláhúzásjeleket szóközökre a megjelenítéshez.
### Eredmény
```javaScript
function betoltKollekciok() {
    const select = document.getElementById('kollekcioSelect');
    
    select.innerHTML = '<option value="">-- Válassz --</option>';
    
    Kollekciok.forEach(kollekcio => {
        if (kollekcio.elemek.length > 1) {
            const option = document.createElement('option');
            option.value = kollekcio.név;
            option.textContent = kollekcio.név.replace(/_/g, ' ');
            select.appendChild(option);
        }
    });
}
```
---
### Prompt
Írj egy függvényt, amely egy adott kollekció elemeit megjeleníti érték szerint csökkenő sorrendben. Minden elemhez generálj képet, és jelenítsd meg az értékét, esélyét és csillagjait.
### Eredmény
```javaScript
function megjelenitElemek(kollekcioNev) {
    const kollekcio = Kollekciok.find(k => k.név === kollekcioNev);
    const container = document.getElementById('elemekContainer');
    
    if (!kollekcio) return;
    const rendezettElemek = [...kollekcio.elemek].sort((a, b) => b.érték - a.érték);
    
    container.innerHTML = rendezettElemek.map(elem => {
        const kepUt = kepElérésiÚt(kollekcio.név, elem.név);
        
        return `
            <div class="elem-doboz ${elem.ritkaság}">
                <div class="elem-kep">
                    <img src="${kepUt}.png" alt="${elem.név}" 
                         onerror="this.src='${kepUt}.jpg'; this.onerror=null;">
                </div>
                <div class="elem-info">
                    <h3>${elem.név}</h3>
                    <p><strong>${elem.érték.toFixed(2)} EUR</strong></p>
                    <p>Esély: <strong>${(elem.esély * 100).toFixed(2)}%</strong></p>
                    <p>Csillag: ${elem.csillag} ⭐</p>
                </div>
            </div>
        `;
    }).join('');
}
```
---
### Prompt
Készíts egy JavaScript függvényt, amely szimulálja a láda nyitását adott számú alkalommal. Normalizáld az esélyeket, válassz véletlenszerűen elemeket az esélyeik alapján, számold ki a költségeket és bevételt, majd jelenítsd meg az eredményeket statisztikákkal együtt.
### Eredmény
```javaScript
function szimulalKollekcio(kollekcio, nyitasokSzama) {
    const eredmenyek = [];
    let osszesKoltseg = 0;
    let osszesBevetel = 0;
    const normalizaltElemek = normalizalEselyek(kollekcio.elemek);
    
    for (let i = 0; i < nyitasokSzama; i++) {
        const kivalasztottElem = kivalasztElem(normalizaltElemek);
        const koltseg = kollekcio.elemek[0].csillag * 0.40;
        const bevetel = kivalasztottElem.érték;
        
        osszesKoltseg += koltseg;
        osszesBevetel += bevetel;
        
        eredmenyek.push({
            sorszam: i + 1,
            elem: kivalasztottElem,
            koltseg: koltseg,
            bevetel: bevetel,
            nyereseg: bevetel - koltseg,
            szorzo: bevetel / koltseg
        });
    }
    
    return {
        reszletek: eredmenyek,
        osszesites: {
            osszesKoltseg: osszesKoltseg,
            osszesBevetel: osszesBevetel,
            osszesNyereseg: osszesBevetel - osszesKoltseg,
            atlagSzorzo: osszesBevetel / osszesKoltseg
        }
    };
}
```
---
### Prompt
Írj egy segédfüggvényt, amely normalizálja az elemek esélyeit, hogy összegük pontosan 1 legyen. Ha az eredeti esélyek összege nem 1, akkor arányosan skálázd őket.
### Eredmény
```javaScript
function normalizalEselyek(elemek) {
    const osszesEsely = elemek.reduce((sum, elem) => sum + elem.esély, 0);
    if (Math.abs(osszesEsely - 1) > 0.001) {
        console.log(`Esélyek normalizálva: ${osszesEsely.toFixed(4)} -> 1.0000`);
        return elemek.map(elem => ({
            ...elem,
            esély: elem.esély / osszesEsely
        }));
    }
    return elemek;
}
```
---
### Prompt
Készíts egy függvényt, amely az elemek esélyei alapján véletlenszerűen kiválaszt egy elemet. Használj kumulatív valószínűségi eloszlást a kiválasztáshoz.
### Eredmény
```javaScript
function kivalasztElem(elemek) {
    let veletlen = Math.random();
    let osszeg = 0;
    
    for (const elem of elemek) {
        osszeg += elem.esély;
        if (veletlen <= osszeg) {
            return elem;
        }
    }
    
    return elemek[elemek.length - 1];
}
```