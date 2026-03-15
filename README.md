# [davelopment]® · FinanceOS

> Gazdasági webalkalmazás demó – értékesítési dashboard, cash flow modell, költségkövető és számlázó egy helyen.

![FinanceOS Demo](https://img.shields.io/badge/demo-live-00e5a0?style=flat-square&logo=github)


---

## 🔴 Élő demó

👉 **[Megnyitás](https://davidvasadi.github.io/financeos/)**

---

## 📦 Modulok

| Modul | Leírás |
|---|---|
| 📊 Értékesítési dashboard | Havi bevételek, top termékek, kategória megoszlás |
| 📈 Cash Flow modell | Interaktív szimuláció, break-even számítás |
| 💰 Költségkövető | Kiadások kezelése kategóriánként, büdzsé követés |
| 🧾 Számlázó | Számlakészítés, tételek, ÁFA számítás |

---

## 🚀 Helyi futtatás

```bash
# 1. Klónozd a repót
git clone https://github.com/FELHASZNALONEV/financeos.git
cd financeos

# 2. Nyisd meg böngészőben
# Dupla kattintás az index.html fájlra
# VAGY helyi szerver indítása:
python -m http.server 8000
# → http://localhost:8000
```

> ⚠️ A `fetch()` hívások miatt ajánlott helyi szervert használni, ne simán fájlból megnyitni.

---

## 🗂️ Projekt struktúra

```
financeos/
├── index.html          ← fő alkalmazás
├── data/
│   ├── dashboard.json  ← értékesítési mock adatok
│   ├── expenses.json   ← kiadás mock adatok
│   └── invoices.json   ← számla mock adatok
└── README.md
```

---

## 🛠️ Tech stack (demó)

- Vanilla HTML / CSS / JavaScript
- Chart.js 4.4 – grafikonok
- Google Fonts – Space Grotesk + Space Mono
- JSON mock adatok – `data/` mappából töltve

## 🐍 Backend feladat (junior)

A demó alapján Flask + SQLite backendet kell implementálni.  
A feladatkiírás részletei a `TASK.md` fájlban.

---

