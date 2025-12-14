Adatvezérelt edzés- és étrendtervezés felhasználói aktivitás alapján

Szakdolgozat - Óbudai Egyetem, Mérnökinformatikus szak

---

## Tartalomjegyzék

- [Leírás](#leírás)
- [Főbb funkciók](#főbb-funkciók)
- [Technológiai stack](#technológiai-stack)
- [Telepítés](#telepítés)
- [Használat](#használat)
- [Projekt struktúra](#projekt-struktúra)
- [Kalória számítás](#kalória-számítás)
- [Adatbázis modellek](#adatbázis-modellek)

---

## Leírás

Az alkalmazás egy személyre szabott fitness és táplálkozás ajánló rendszer, amely tudományos alapokon nyugvó kalória- és makrotápanyag számításokat végez. A rendszer figyelembe veszi a felhasználó egyéni adatait, munkarendjét, alvási szokásait és edzési céljait a pontos ajánlások érdekében.



###  Felhasználó kezelés
- Regisztráció és bejelentkezés
- Többlépcsős profil kitöltés
- Személyes adatok és célok beállítása

###  Kalória & Makró számítás
- BMR számítás (Mifflin-St Jeor formula)
- TDEE meghatározás aktivitási szint alapján
- Személyre szabott makrotápanyag arányok
- Heti/havi program támogatás

### 🏃Edzés követés
- Cardio edzések naplózása (séta, futás, kerékpár, úszás)
- Napi check-in rendszer
- Heti és havi összesítők
- Haladás követés

###  Recept ajánló
- Kalória és makró alapú receptajánlás
- Kedvenc receptek kezelése
- Saját receptek hozzáadása
- Étkezés kategóriák (reggeli, ebéd, vacsora, snack)

###  Statisztikák
- Napi/heti/havi összesítők
- Súlyváltozás követés
- Lépésszám és távolság statisztikák
- Vizuális grafikonok
- 
## 🛠 Technológia

| Komponens | Technológia |
|-----------|-------------|
| Backend | Python 3.13, Flask 3.0 |
| Adatbázis | SQLite + SQLAlchemy ORM |
| Frontend | Jinja2, Bootstrap 5, CSS3 |
| Authentikáció | Flask-Login |
| Form kezelés | Flask-WTF, WTForms |



##  Használat

### Első lépések

1. **Regisztráció** - Felhasználónév és jelszó megadása
2. **Profil kitöltés** - 4 lépéses varázsló:
   - Alapadatok (kor, nem, magasság, súly)
   - Munkarend és alvási szokások
   - Célok beállítása (fogyás/izomépítés/karbantartás)
   - Edzési preferenciák
3. **Dashboard** - Személyre szabott napi célok megtekintése
4. **Napi check-in** - Napi adatok rögzítése

### Napi használat

- Reggel: Súlymérés rögzítése
- Napközben: Étkezések és lépések naplózása
- Edzés után: Edzés adatok rögzítése
- Este: Napi összesítő megtekintése



## 📁 Projekt struktúra

```
fitness_app/
├── app/
│   ├── __init__.py          # App factory, DB inicializálás
│   ├── forms.py             # WTForms űrlapok
│   ├── models/
│   │   └── user.py          # SQLAlchemy modellek
│   ├── routes/
│   │   ├── auth.py          # Authentikáció, profil
│   │   ├── recipes.py       # Recept kezelés
│   │   └── workouts.py      # Edzés, check-in, dashboard
│   ├── static/
│   │   ├── css/
│   │   │   └── style.css    # Egyedi stílusok
│   │   └── js/
│   │       └── main.js      # JavaScript funkciók
│   └── templates/           # Jinja2 sablonok
│       ├── base.html
│       ├── auth/
│       ├── recipes/
│       └── workouts/
├── instance/
│   └── fitness_app.db       # SQLite adatbázis
├── recipes_seed.json        # Recept seed adatok
├── config.py                # Konfiguráció
├── requirements.txt         # Függőségek
├── run.py                   # Belépési pont
└── README.md
```

---

##  Kalória számítás

### BMR (Alapanyagcsere) - Mifflin-St Jeor formula

**Férfi:**
```
BMR = 10 × súly(kg) + 6.25 × magasság(cm) - 5 × kor + 5
```

**Nő:**
```
BMR = 10 × súly(kg) + 6.25 × magasság(cm) - 5 × kor - 161
```

### TDEE (Napi energiafelhasználás)

```
TDEE = BMR × PAL + Munka Extra + NEAT
```

| PAL szorzó | Aktivitási szint |
|------------|------------------|
| 1.2 | Ülő (irodai munka) |
| 1.375 | Könnyű aktivitás |
| 1.55 | Közepes aktivitás |
| 1.725 | Nehéz fizikai munka |
| 1.9 | Nagyon nehéz munka |



### Kalória célok

| Cél | Kalória módosítás |
|----|-------------------|
| Fogyás | TDEE - 500 kcal |
| Karbantartás | TDEE |
| Izomépítés | TDEE + 300 kcal |

---


## 📊 MVC Architektúra

| Réteg | Mappa | Leírás |
|-------|-------|--------|
| Model | `app/models/` | SQLAlchemy ORM, adatvalidáció |
| View | `app/templates/` | Jinja2 sablonok, template öröklődés |
| Controller | `app/routes/` | Flask Blueprints, HTTP kérés kezelés |
## 🔗 Kapcsolat

Barta Péter - Óbudai Egyetem, Mérnökinformatikus szak
