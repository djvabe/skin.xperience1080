# Xperience1080 „2026" — telepítés az iMac-en futó Kodiba

Részletes útmutató a skin telepítéséhez **macOS-en** (cél: iMac 27" 2012, macOS Catalina 10.15.8, GTX 680MX, Kodi 21 *Omega*). Windowsra a 6. pont végén van külön megjegyzés.

> **Fontos:** ez a skin a **`script.skinshortcuts`** kiegészítőtől függ (a testreszabható főmenühöz és a hubonkénti widgetekhez). Ezt **a skin engedélyezése ELŐTT** telepíteni kell, különben a Kodi „Hiányzó függőség" hibával nem engedi aktiválni. Lásd 2. pont.

---

## 0. Mire lesz szükség
- **Kodi 21 Omega** (vagy 22 Piers beta) telepítve a macOS-en.
- A skin fájljai. Két forrásból szerezheted be (1. pont): GitHub fork ág, vagy a helyi munkamásolat.
- Internet a `script.skinshortcuts` letöltéséhez a hivatalos Kodi repóból.

---

## 1. A skin fájljainak beszerzése

A munka jelenleg a fork **`remake-2026`** ágán van (még nincs a `main`-be olvasztva). Válassz:

**A) GitHub-ról (ha az ág már fel van töltve):**
```bash
git clone https://github.com/djvabe/skin.xperience1080.git
cd skin.xperience1080
git checkout remake-2026
```
vagy töltsd le ZIP-ként a GitHub‑ról: *Code ▸ Download ZIP* a `remake-2026` ágon, majd csomagold ki.

**B) A jelenlegi munkamásolatból** (ez a gép): a teljes mappa itt van:
```
D:\tmp\skin.xperience1080
```
Másold át egészben (pendrive / hálózat / felhő) az iMac-re.

A mappa neve **maradjon pontosan** `skin.xperience1080`.

---

## 2. A függőség telepítése (`script.skinshortcuts`) — KÖTELEZŐ ELSŐ LÉPÉS

A Kodi-ban (még a régi skinnel):
1. **Beállítások ▸ Kiegészítők ▸ Telepítés tárolóból** (Install from repository)
2. **Kodi Add-on repository ▸ Program-kiegészítők** (Program add-ons)
3. Keresd ki: **Skin Shortcuts** → **Telepítés**.

Ez Omegán a **2.0.3**-as verziót telepíti (pontosan ezt importálja a skin `addon.xml`-je). Ha kész, mehet a 3. pont.

---

## 3. A skin bemásolása a Kodi addons mappájába

macOS-en a Kodi felhasználói adatai itt vannak:
```
~/Library/Application Support/Kodi/
```
(A `~/Library` rejtett: a Finderben **Cmd+Shift+G**, és írd be az útvonalat.)

Másold a teljes `skin.xperience1080` mappát ide:
```
~/Library/Application Support/Kodi/addons/skin.xperience1080
```
Az eredmény így nézzen ki:
```
~/Library/Application Support/Kodi/addons/skin.xperience1080/addon.xml
~/Library/Application Support/Kodi/addons/skin.xperience1080/1080i/
~/Library/Application Support/Kodi/addons/skin.xperience1080/colors/
~/Library/Application Support/Kodi/addons/skin.xperience1080/fonts/
...
```

> **Terminál-paranccsal** (ha a letöltött mappa a `~/Downloads`-ban van):
> ```bash
> cp -R ~/Downloads/skin.xperience1080 "$HOME/Library/Application Support/Kodi/addons/"
> ```

**ZIP-ből telepítés helyett** ezt a közvetlen másolást ajánlom fejlesztéshez, mert a ZIP‑telepítő nem oldja fel automatikusan a függőségeket. (Ha mégis ZIP kell: csomagold a mappát `skin.xperience1080-11.0.0.zip` néven úgy, hogy a zipben a `skin.xperience1080/` mappa legyen a gyökér, majd **Telepítés zip-fájlból** — de előbb a 2. pont legyen kész.)

---

## 4. A skin engedélyezése
1. Indítsd újra a Kodit (vagy: **Beállítások ▸ Kiegészítők ▸ Saját kiegészítők ▸ Felületi témák**).
2. **Beállítások ▸ Felület ▸ Felületi téma (Skin)** → válaszd: **Xperience1080**.
3. A Kodi rákérdez a váltásra → **Igen**. (Ha „régi" Xperience volt fent, ez ugyanaz az addon-id, csak az új verzió.)

Ha hiányzó-függőség hibát ír: a 2. pont kimaradt — telepítsd a Skin Shortcuts-ot.

---

## 5. Beállítások a 2012-es iMac-hez (GPU-kímélő)

Az erőforrás-igényes effektek alapból KI vannak kapcsolva, de ellenőrizd:
- **Beállítások ▸ Felület ▸ Felületi téma ▸ Beállítások** (a skin saját beállításai).
- A **„Mozgó háttér" (MotionFX)** legyen **KI** — ez kapcsolja a Ken Burns zoomot és a háttér-animációt. A 680MX-en így gördülékenyebb.
- **Kiemelő szín** (accent): **Beállítások ▸ Felület ▸ Felületi téma ▸ Színek** alatt válthatsz kék / borostyán / smaragd / lila / korall között (ezek a `colors/` témafájlok).

A betűk (Sora, Manrope) a skinbe csomagolva érkeznek (`fonts/`), nem kell rendszerszinten telepíteni — macOS és Windows alatt egyformán működik.

---

## 6. Szerkesztés és újratöltés (ha tovább fejleszted)
- A skin XML-jeit a `~/Library/Application Support/Kodi/addons/skin.xperience1080/1080i/` alatt szerkesztheted.
- Újratöltés Kodi-újraindítás nélkül: kösd egy gombra vagy futtasd a **`ReloadSkin()`** beépített parancsot (pl. távoli `kodi-send -a "ReloadSkin()"`).
- Hibák megtekintése (macOS Kodi-log):
  ```
  ~/Library/Logs/kodi.log
  ```
  Itt látszik, ha egy include/control/textúra hiányzik.

> **Windows-on** ugyanez, csak az útvonalak mások:
> - addons mappa: `%APPDATA%\Kodi\addons\skin.xperience1080`
> - log: `%APPDATA%\Kodi\kodi.log`
> A skin XML-jei, betűi, színei azonosak — a skin szándékosan **univerzális** (relatív útvonalak, csomagolt betűk, kis/nagybetű-pontos textúranevek).

---

## 7. Ismert állapot / hibakeresés
- **A főmenü üres vagy nem szerkeszthető:** a `script.skinshortcuts` nincs telepítve/engedélyezve (2. pont). Az első indításkor a `shortcuts/mainmenu.DATA.xml` alapján épül fel a menü (Kezdőlap, Filmek, Sorozatok, Élő TV, Kiegészítők). A „+" gombbal (jobb felül) nyílik a menüszerkesztő.
- **A widget-csempék üresek:** alapból a helyi Kodi-könyvtárból és a PVR-ből töltenek (nemrég hozzáadott filmek/epizódok, csatornák). Ha nincs könyvtár vagy PVR beállítva, üresek maradnak — a widget-kezelőben átállíthatók (pl. Jellyfin/IPTV mappára).
- **Hiányzó ikon/kép:** nézd a `kodi.log`-ot „missing texture" sorokért. A jelenlegi Home a meglévő skin-textúrákat használja; néhány ikon a következő fázisban kap végleges PNG-t.
- **Ez egy fejlesztés alatti remake:** jelenleg a **Kezdőlap (Tiles)** képernyő van átdolgozva. A többi képernyő (könyvtár-fal, részletek, lejátszó OSD, Élő TV, keresés, beállítások) még a régi Xperience kinézetet hozza, amíg a további fázisok elkészülnek.
