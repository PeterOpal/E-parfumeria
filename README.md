# E-parfuméria — Online obchod s parfumami
 
**Autor:** Peter Opal  
**Licencia:** Súkromný projekt  
**Šablóna:** [Zay Shop](https://themewagon.com/themes/free-bootstrap-5-html-5-ecommerce-website-template-zay-shop/) (ThemeWagon)
 
 
## Popis projektu
 
**E-parfuméria** je moderná jednostránková webová aplikácia (SPA) typu e-shop, zameraná na predaj luxusných parfumov. Aplikácia je postavená na frameworku **Vue 3** s využitím nástroja **Vite** ako build systému. Ponúka kompletný nákupný zážitok. Ood prehliadania produktov, cez filtrovanie a triedenie, až po správu nákupného košíka s checkout procesom.
 
Projekt simuluje reálny e-shop s parfumami od svetových značiek ako **BVLGARI, Versace, Gucci, Dior** atď. Dáta produktov sú uložené lokálne v JSON súbore (bez backendu).
 
---
 
## Použité technológie
 
| Technológia | Verzia | Účel |
|---|---|---|
| **Vue.js 3** | ^3.4.15 | Hlavný frontend framework (SPA) |
| **Vite** | ^5.0.10 | Build nástroj a vývojový server |
| **Vue Router** | ^4.2.5 | Smerovanie (routing) medzi stránkami |
| **Pinia** | ^2.1.7 | Správa stavu aplikácie (state management) |
| **Vuetify** | ^3.4.9 | UI komponentová knižnica (Material Design) |
| **Bootstrap 5** | (zahrnutý v CSS) | Responzívny layout a grid systém |
| **Font Awesome** | (zahrnutý v CSS) | Ikony (sociálne siete, navigácia, služby) |
| **Material Design Icons** | ^7.4.47 | Ikony pre Vuetify komponenty |
| **jQuery** | 1.11.0 | Pomocné DOM operácie (legacy) |
| **vue-countdown** | ^2.1.2 | Odpočítavacie hodiny pre zľavovú akciu |
| **Google Fonts (Roboto)** | (CDN) | Typografia celej aplikácie |
| **Google Maps Embed API** | (iframe) | Mapa na kontaktnej stránke |
| **@vitejs/plugin-vue** | ^4.5.2 | Vite plugin pre spracovanie Vue SFC súborov |
 
---
 
## Štruktúra projektu
 
```
ft/
├── index.html                  # Vstupný HTML súbor
├── package.json                # Závislosti a skripty
├── vite.config.js              # Konfigurácia Vite
├── jsconfig.json               # Konfigurácia JavaScript (aliasy)
├── .gitignore                  # Ignorované súbory pre Git
├── .vscode/                    # Nastavenia VS Code
└── src/
    ├── main.js                 # Vstupný bod aplikácie (Vue, Pinia, Vuetify, Router)
    ├── App.vue                 # Koreňový komponent aplikácie
    ├── router/
    │   └── index.js            # Definícia smerovania (routes)
    ├── stores/
    │   └── CartStore.js        # Pinia store pre nákupný košík
    ├── views/
    │   ├── MainView.vue        # Domovská stránka (carousel, top vône, zľava)
    │   ├── Shop.vue            # Obchod — výpis produktov s filtrami
    │   ├── ProductView.vue     # Detail produktu
    │   ├── ShoppingCart.vue    # Nákupný košík s checkout dialogom
    │   ├── AboutView.vue       # O nás — popis služieb a značiek
    │   └── Contact.vue         # Kontakt — formulár a Google mapa
    ├── components/
    │   ├── TheNavigation.vue   # Horný navigačný panel
    │   ├── TheFooter.vue       # Pätička stránky
    │   ├── ProductCard.vue     # Karta produktu (obrázok, cena, hodnotenie)
    │   ├── Rating.vue          # Hviezdičkové hodnotenie
    │   ├── SearchModal.vue     # Modálne okno pre vyhľadávanie
    │   ├── BrandsCarousel.vue  # Karusel so značkami
    │   └── ServicesCard.vue    # Karta služby
    └── assets/
        ├── data.json           # Dáta produktov (14 parfumov)
        ├── css/                # Štýly (Bootstrap, FontAwesome, šablóna)
        ├── js/                 # JavaScript knižnice (jQuery, Bootstrap, Slick)
        ├── img/                # Obrázky produktov a značiek
        └── webfonts/           # Fonty ikon (FontAwesome, Slick)
```
 
---
 
## Stránky a funkcie
 
### 1. Domovská stránka (`/`)
- **Karusel** so 4 slidmi — propagačné texty a obrázky
- Sekcia **„Fragrances of The Year"** — top 3 vône s odkazom na obchod
- **Odpočítavanie** do konca zľavovej akcie (vue-countdown)
- **Zľavový kód** „VERSACE" — kliknutím sa skopíruje do schránky
 
### 2. Obchod (`/shop`)
- Zobrazenie **14 produktov** vo forme kariet
- **Filtrovanie** podľa pohlavia (Muži / Ženy / Všetky)
- **Triedenie** podľa ceny (od najnižšej / od najvyššej)
- Každá karta obsahuje: obrázok, názov, kategóriu, hviezdičkové hodnotenie a cenu
- Tlačidlo na rýchle pridanie do košíka
- Sekcia **„Our Brands"** — karusel so značkami (Versace, Gucci, Tom Ford, Dior, Prada, Dolce&Gabbana)
 
### 3. Detail produktu (`/shop/product?id=...`)
- Veľký obrázok produktu
- Názov, cena, hodnotenie (z magazínu Fragratica), značka, popis, špecifikácie (pohlavie, objem)
- **Výber množstva** s obmedzením (max 15 položiek v košíku celkovo)
- Tlačidlo **„Add To Cart"**
- Ochrana proti neexistujúcemu produktu (chybová správa)
 
### 4. Nákupný košík (`/shoppingCart`)
- **Tabuľka** so všetkými položkami v košíku
- Zvyšovanie/znižovanie množstva (+/-)
- Odstránenie položky z košíka
- Zobrazenie **ceny za kus** a **celkovej ceny**
- Maximálny limit: **15 parfumov** v jednom košíku
- **Checkout dialóg** (Vuetify dialog) s poliami:
  - Meno, priezvisko, e-mail, telefón, adresa, PSČ, kupón
  - Výber dopravy: DHL / Post
  - Výber platby: Crypto / Credit Card / Debit Card / PayPal
- *Poznámka: Backend nie je implementovaný — po kliknutí na „Pay" sa košík resetuje*
 
### 5. O nás (`/about`)
- Popis spoločnosti **E-parfuméria**
- Sekcia **„Our Services"** — 4 služby (Doručenie, Vrátenie, Akcie, 24h servis)
- Karusel značiek
 
### 6. Kontakt (`/contact`)
- **Google Maps** — interaktívna mapa Bratislavy
- **Kontaktný formulár** (meno, e-mail, predmet, správa)
- *Poznámka: Formulár je zatiaľ deaktivovaný (tlačidlo disabled)*
 
---
 
## Správa stavu (Pinia Store)
 
Nákupný košík je spravovaný cez **Pinia store** (`CartStore.js`):
 
| Akcia | Popis |
|---|---|
| `addItemToCart(id)` | Pridanie 1 ks produktu do košíka |
| `addItemToCartWithQuantity(id, qty)` | Pridanie produktu so zvoleným množstvom |
| `incrementQuantity(id)` | Zvýšenie množstva o 1 |
| `decrementQuantity(id)` | Zníženie množstva o 1 (min. 1) |
| `removeItemFromCart(id)` | Odstránenie produktu z košíka |
| `total` (getter) | Celkový počet položiek v košíku |
 
**Maximálny limit košíka:** 15 položiek celkovo.
 
---
 
## Inštalácia a spustenie
 
### Požiadavky
- **Node.js** (odporúčaná verzia 18+)
- **npm** (správca balíkov)
 
### Inštalácia závislostí
```sh
npm install
```
 
### Spustenie vývojového servera
```sh
npm run dev
```
Aplikácia bude dostupná na `http://localhost:5173` (predvolený port Vite).
 
---
 
## Odporúčané vývojové prostredie
 
- **IDE:** [Visual Studio Code](https://code.visualstudio.com/)
- **Rozšírenia:** [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) 
 
