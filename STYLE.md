# GTA VI — Stílusirány

## Megjelenés

GTA VI / Vice City hangulat: naplementés színek, pálmafák,
karakteres címek és letisztult kezelőfelület.

- A háttérkép maradjon látható.
- A kártyák, menük és panelek áttetsző, sötét hátteret kapjanak.
- Finom háttérelmosás, vékony keretek, visszafogott neonkiemelések.
- Az autóadatbázis és a térkép esetén az olvashatóság az első.

## Színek

- Alap: `#0F0F0F`
- Szöveg: `#FFFFFF`
- Elsődleges kiemelés: `#FF2D55`
- Kiegészítők: `#EB9998`, `#5D549C`, `#6F70A2`,
  `#7E3A63`, `#A373D3`
- Áttetsző panelek: `rgba(15, 15, 15, 0.75)`
- Finom keretek: `rgba(255, 255, 255, 0.12)`

![Színpaletta](assets/style/color-palette.png)

## Betűtípusok

- **Bebas Neue:** nagy címek, szekciócímek.
- **Roboto:** szövegek, navigáció, gombok és adatok.
- Törzsszöveg: 16 px; kisebb feliratok: 14 px.

![Stílus és tipográfia](assets/style/style-reference.png)

## Háttér és képek

A naplementés kép a főoldal háttere. Szöveg alatt sötét,
áttetsző fedőréteg biztosítsa az olvashatóságot.

![Naplementés háttér](assets/style/sunset-background.png)

A logós képet teljes képaránnyal, levágás és ráhelyezett szöveg
nélkül használjuk kiemelt illusztrációként.

![GTA VI logós illusztráció](assets/style/gta-vi-logo.png)

## Komponensek

- **Fejléc:** áttetsző sötét felület, aktív menüpont rózsaszínnel.
- **Gombok:** rózsaszín elsődleges, áttetsző másodlagos változat.
- **Kártyák:** 12–16 px lekerekítés, finom keret, egységes autóképek.
- **Adatbázis:** kereső, szűrők és reszponzív kártyarács.
- **Térkép:** nagy térképfelület, áttetsző kezelőpanelek;
  mobilon alulról nyitható részletek.
- **Animációk:** rövid, 150–250 ms átmenetek.

Mobilon egyoszlopos elrendezés, jól érinthető gombok és összecsukható
szűrők legyenek. Minden interaktív elem kapjon látható fókuszállapotot.
