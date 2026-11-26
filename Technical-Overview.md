<p align="center">
  <a href="./README.md"><strong>📖 Projekt Áttekintés</strong></a> &nbsp;·&nbsp;
  <strong>⚙️ Technikai Áttekintés</strong> &nbsp;·&nbsp;
  <a href="#1-tech-stack">Tech Stack</a> &nbsp;·&nbsp;
  <a href="#2-gta-6-térkép-2d---3d-implementációs-terv">2D → 3D Térkép Terv</a>
</p>

---

# Technikai Áttekintés (Technical Overview)

> Fókuszban a **Web** és a **Backend** fejlesztés. A mobilos alkalmazások az utolsó fázisban épülnek a kész API-ra.

---

## 1. Tech Stack

### Web (Frontend)

- **Keretrendszer:** React (Vite)
- **Stílus:** Tailwind CSS
- **Térképmotor:** `react-map-gl` + **MapLibre GL JS** (WebGL alapú 2D/3D megjelenítés)

### Backend és Adatbázisok

- **Szerver / API:** Node.js + **Express.js** (REST API, JWT hitelesítés)
- **PostgreSQL (Elsődleges adatbázis):** Relációs adatok (felhasználók, járművek, küldetések, felhasználói előrehaladás, garázs).
- **MongoDB (Térképi és rugalmas adatok):** Térképi **GeoJSON** rétegek (3D épületek alaprajzai, magassága, koordinátái), közösségi beküldések és naplók.
- **SQLite (Helyi / Offline tároló):** Gyors helyi fejlesztői környezet, illetve a későbbi mobilkliensek offline gyorsítótára.

### Mobil (Utolsó fázis)

- **iOS:** SwiftUI
- **Android:** Natív Android (Kotlin) vagy Angular (Ionic/Capacitor)

---

## 2. GTA 6 Térkép (2D -> 3D) Implementációs Terv

A cél egy olyan térkép, amely távolról a klasszikus 2D-s GTA térképére hasonlít, rázoomoláskor viszont megdől a kamera, és az épületek 3D-ben kiemelkednek.

### A) Hogyan hasonlít 1:1-ben a GTA 6 térképre?

1. **Egyedi Alaptérkép (Basemap):**
   - Saját GTA 6 színséma (Style JSON): sötétkék/türkiz víz, sötétszürke szárazföld, Vice City neon-rózsaszín és cián főutak, vagy csempékre (`tiles/{z}/{x}/{y}.png`) vágott egyedi GTA 6 térkép.
2. **GTA HUD és Radar Ikonok (Blips):**
   - Tailwind CSS-szel a térkép fölé rétegezett GTA 6 stílusú oldalsáv, koordináta-kijelző, célkereszt és egyedi SVG radar-ikonok.

### B) Hogyan működik a 2D -> 3D Zoom és Épület-kiemelkedés?

1. **Adatforrás (MongoDB -> Express -> React):**
   - Az épületek alaprajzai **GeoJSON `Polygon`** formátumban vannak tárolva, mindegyikhez tartozik egy `height` (magasság méterben) és egy `color` tulajdonság.
2. **Távoli nézet (`zoom < 14`):**
   - A kamera felülnézeti (`pitch: 0°`), az épületek magassága `0` (sík 2D térkép).
3. **Közelítés (`zoom: 14 -> 16`):**
   - **Kamera döntés:** Zoomoláskor a kamera dőlésszöge (`pitch`) automatikusan `0°`-ról `55°`-ra vált.
   - **3D Kihúzás (`fill-extrusion`):** A MapLibre `interpolate` kifejezése a zoom szint alapján fokozatosan `0`-ról a valódi magasságukra (`height`) emeli ki az épületeket.

---

### D) Megvalósítási Lépések (Térkép)

- [ ] 1. Alap `react-map-gl` + MapLibre komponens bekötése egyedi GTA 6 sötét/neon stíluslappal
- [ ] 2. GeoJSON épület-adatok (poligonok + magasságok) kiszolgálása Express + MongoDB végpontról
- [ ] 3. `fill-extrusion` réteg és zoom-alapú kamera döntés (`pitch`) beállítása
- [ ] 4. Kattintható markerek (Blips) és 3D épületek összekötése a React oldalsávval
