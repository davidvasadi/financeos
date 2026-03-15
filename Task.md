# Feladatkiírás – FinanceOS Flask backend

## Cél

A fenti demó alapján készítsd el ugyanezt az alkalmazást **Python + Flask** segítségével.
A frontend (`index.html`) már meg van csinálva – a te feladatod a **backend és az adatréteg**.

---

## Tech stack

| Réteg | Technológia |
|---|---|
| Backend | Python 3.10+, Flask 3.0 |
| Adatbázis | SQLite + SQLAlchemy |
| PDF export | ReportLab |
| Mock adatok | Faker |
| Frontend | A kapott `index.html` (ne módosítsd) |

**Csomagok – requirements.txt:**
```
flask==3.0.0
flask-sqlalchemy==3.1.1
flask-cors==4.0.0
reportlab==4.1.0
faker==24.0.0
```

---

## Projekt struktúra

```
financeos-flask/
├── app/
│   ├── __init__.py        ← app factory (create_app)
│   ├── models.py          ← SQLAlchemy modellek
│   ├── routes/
│   │   ├── main.py        ← / főoldal
│   │   ├── dashboard.py   ← /api/dashboard
│   │   ├── cashflow.py    ← /api/cashflow
│   │   ├── expenses.py    ← /api/expenses CRUD
│   │   └── invoices.py    ← /api/invoices + PDF
│   └── templates/
│       └── index.html     ← a kapott demó HTML
├── seed.py                ← adatbázis feltöltés Faker-rel
├── config.py              ← konfiguráció, DB útvonal
├── run.py                 ← belépési pont
└── requirements.txt
```

---

## API végpontok

| Metódus | URL | Leírás |
|---|---|---|
| GET | `/api/dashboard` | Bevételek, top termékek, kategóriák |
| GET | `/api/cashflow` | Cash flow szimuláció (query paraméterekkel) |
| GET | `/api/expenses` | Összes kiadás |
| POST | `/api/expenses` | Új kiadás hozzáadása |
| DELETE | `/api/expenses/<id>` | Kiadás törlése |
| PUT | `/api/expenses/<id>` | Kiadás szerkesztése |
| GET | `/api/invoices` | Összes számla |
| POST | `/api/invoices` | Új számla létrehozása |
| PUT | `/api/invoices/<id>` | Számla frissítése |
| GET | `/api/invoices/<id>/pdf` | PDF letöltés |

---

## Telepítés és indítás

```bash
# 1. Virtuális környezet
python -m venv venv
venv\Scripts\activate        # Windows
source venv/bin/activate     # Mac/Linux

# 2. Csomagok
pip install -r requirements.txt

# 3. Adatbázis feltöltése
python seed.py

# 4. Szerver indítás
flask run --debug
# → http://localhost:5000
```

---

## Értékelési szempontok

| Szempont | Súly |
|---|---|
| Működő Flask API végpontok | 30% |
| SQLite adatbázis + SQLAlchemy modellek | 20% |
| Kódminőség (Blueprint struktúra, PEP8, kommentek) | 20% |
| Frontend integráció (az API-ból tölt adatot) | 15% |
| README + GitHub (telepítési leírás, képernyőképek) | 10% |
| Bónusz: PDF export (ReportLab) | +5% |

---

## 🌐 Online deploy – Render (ingyenes)

Hogy az interjún egy kattintással meg lehessen mutatni, deploy-old fel a **Render** platformra – teljesen ingyenes.

**1. Készítsd el a `render.yaml` fájlt a projekt gyökerébe:**
```yaml
services:
  - type: web
    name: financeos
    runtime: python
    buildCommand: "pip install -r requirements.txt && python seed.py"
    startCommand: "flask run --host=0.0.0.0 --port=10000"
    envVars:
      - key: FLASK_APP
        value: run.py
      - key: FLASK_ENV
        value: production
```

**2. Készítsd el a `Procfile` fájlt:**
```
web: flask run --host=0.0.0.0 --port=$PORT
```

**3. Deploy lépések:**
1. Menj a [render.com](https://render.com) oldalra → regisztrálj GitHub fiókkal
2. **New → Web Service**
3. Kapcsold össze a `financeos-flask` repódat
4. Render automatikusan felismeri a `render.yaml`-t
5. Kattints a **Deploy** gombra
6. Pár perc múlva kapsz egy ilyen linket: `https://financeos.onrender.com`

> ⚠️ Az ingyenes Render szerver ~15 perc inaktivitás után "elalszik" – az első betöltés 30-60 másodpercig tarthat. Ez normális az ingyenes tervnél.

---

## Beadás

- GitHub repository neve: `financeos-flask`
- Legalább **10 commit** legyen – ne egyszerre töltsd fel
- README.md legyen részletes, képernyőképekkel

---

© 2026 [davelopment]®
