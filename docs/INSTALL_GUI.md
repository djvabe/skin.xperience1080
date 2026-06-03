# Telepítés a Kodi grafikus felületén (ZIP-ből)

Ez az útmutató **kizárólag a Kodi GUI-ján keresztül**, a beépített *„Telepítés zip-fájlból"* funkcióval telepíti az **Xperience1080 „2026"** skint. Működik **Windowson és macOS-en** (és Linuxon) egyformán.

---

## Amire szükséged van
1. **A telepítő ZIP:** `skin.xperience1080-11.0.0.zip`
   (a projektmappában: `d:\2026-work\KODI_HOBBI\skin.xperience1080-11.0.0.zip`).
   Másold át a Kodi-t futtató gépre (pl. iMac) bárhová — pl. az asztalra vagy a Letöltések mappába.
2. **Internetkapcsolat** a Kodin: a skin függ a **Skin Shortcuts** kiegészítőtől, amit a Kodi a telepítéskor **automatikusan letölt** a hivatalos tárolóból.

---

## 1. lépés — „Ismeretlen források" engedélyezése
A Kodi alapból tiltja a ZIP-ből telepítést, ezt egyszer engedélyezni kell:

**Beállítások (fogaskerék) ▸ Rendszer ▸ Kiegészítők ▸ Ismeretlen források** → kapcsold **BE**.
> *Settings ▸ System ▸ Add-ons ▸ Unknown sources* → ON. A figyelmeztetésnél nyomj **Igen**-t.

---

## 2. lépés — Telepítés a ZIP-ből
1. **Beállítások ▸ Kiegészítők ▸ Telepítés zip-fájlból**
   *(Settings ▸ Add-ons ▸ Install from zip file)*
2. Tallózd ki, hová másoltad a fájlt, és válaszd ki:
   **`skin.xperience1080-11.0.0.zip`**
3. A Kodi elkezdi a telepítést, és **magától feloldja a függőséget** (Skin Shortcuts) a hivatalos tárolóból.
4. Várd meg a jobb felül megjelenő **„A kiegészítő telepítve" / „Add-on installed"** értesítést.

---

## 3. lépés — A skin aktiválása
1. **Beállítások ▸ Felület ▸ Felületi téma (Skin)**
   *(Settings ▸ Interface ▸ Skin)*
2. Válaszd: **Xperience1080**.
3. A Kodi rákérdez a váltásra → **Igen / Keep**.

Készen vagy — betölt az új **Kezdőlap (Tiles)**.

---

## 4. lépés — Első indítás & ajánlott beállítások
- A főmenü a beépített alapból épül fel: **Kezdőlap, Filmek, Sorozatok, Élő TV, Kiegészítők**. A jobb felső **„+"** gombbal szerkeszthető (Skin Shortcuts menükezelő).
- **Gyenge GPU-hoz (pl. 2012 iMac):** *Beállítások ▸ Felület ▸ Felületi téma ▸ Beállítások ▸ Megjelenés 2026* → a **Mozgó háttér** legyen **KI**.
- **Szövegméret:** *Beállítások ▸ Felület ▸ Felületi téma ▸ Betűtípusok* → **Default / Large / Extra**.
- **Kiemelő szín:** *Beállítások ▸ Felület ▸ Felületi téma ▸ Színek* → kék / borostyán / smaragd / lila / korall.

---

## Hibakeresés

**„Hiányzó függőség: script.skinshortcuts" hiba telepítéskor**
A Kodi nem érte el a tárolót (nincs net, vagy ki van kapcsolva a hivatalos repo). Megoldás: telepítsd előbb kézzel:
**Beállítások ▸ Kiegészítők ▸ Telepítés tárolóból ▸ Kodi Add-on repository ▸ Program-kiegészítők ▸ Skin Shortcuts ▸ Telepítés**, majd ismételd a 2. lépést.

**Nem találom a „Telepítés zip-fájlból"-t**
Az 1. lépés (Ismeretlen források) kimaradt — kapcsold be, és próbáld újra.

**A widget-csempék üresek**
Alapból a helyi Kodi-könyvtárból és a PVR-ből töltenek (nemrég hozzáadott filmek/epizódok, csatornák). Ha nincs könyvtár/PVR beállítva, üresek — a menüszerkesztőben átállíthatók add-on mappára (Jellyfin, IPTV, YouTube…).

**Naplófájl** (ha valami nem stimmel):
- macOS: `~/Library/Logs/kodi.log`
- Windows: `%APPDATA%\Kodi\kodi.log`

---

## Megjegyzés
- Ez egy fejlesztés alatti remake: jelenleg a **Kezdőlap (Tiles)** van átdolgozva a 2026 dizájnra; a többi képernyő még a klasszikus Xperience kinézetet hozza.
- Frissítéskor csak telepítsd újra az új ZIP-et (a 2. lépés) — a Kodi felülírja a régi verziót, a beállításaid megmaradnak.
- Kézi (mappás) telepítést és fejlesztői infókat lásd: `docs/TELEPITES_IMAC.md`.
