# SERF — Serf-Pages

## Propòsit del repositori

Aquest repositori conté **exclusivament les pàgines públiques** del projecte SERF, publicades via GitHub Pages des de la branca `main`. El codi de l'aplicació Rails es troba a un repositori separat (Serf-APP).

Contingut actual:
- `index.html` — landing amb enllaços als diagrames
- `diagrama_arquitectura.html` — diagrama estàtic de capes del sistema
- `diagrama_flux.html` — diagrama de flux d'una petició HTTP a través del stack MVC

## Projecte SERF — Context

Aplicació web de gestió de menús per a restaurants que filtra plats per restriccions alimentàries dels comensals.

**Funcionalitats core:**
- CRUD de menús, plats, ingredients i restriccions alimentàries
- Motor de suggeriments: donat un conjunt de restriccions, mostra els plats compatibles i proposa alternatives
- Gestió d'usuaris amb autenticació i tres rols: `admin`, `cuiner`, `cambrer`

**Stack tecnològic (Serf-APP):**
- Framework: Ruby on Rails (MVC)
- Vistes: ERB + Hotwire (Turbo Drive, Turbo Frames, Turbo Streams, Stimulus)
- CSS: per decidir (Bootstrap / Bulma / Tailwind)
- BD: MySQL / MariaDB
- Autenticació: Devise o Rodauth (per decidir)
- Motor de suggeriments: Service Object (`SuggestionService`)
- Tests: MiniTest

**Models principals:**
- `Menu` → has_many :plats
- `Plat` → belongs_to :menu, has_many :ingredients (via join table `plat_ingredients`, amb flag `imprescindible`)
- `Ingredient` → has_many :restriccions, has_many :substituts
- `Restriccio` → intoleràncies, al·lèrgies, preferències
- `Usuari` → rol: admin / cuiner / cambrer

## Convencions d'aquest repositori (Serf-Pages)

- Tots els fitxers HTML segueixen el mateix sistema de disseny: fons fosc (`#0d1117`), tipografies JetBrains Mono + Syne, paleta de colors per capa (blau=client, verd=presentació, lila=aplicació, taronja=domini, vermell=BD).
- Els diagrames són HTML+SVG/CSS purs, sense frameworks ni dependències locals.
- Idioma dels fitxers: català (ca).
- No afegir fitxers de build, node_modules ni cap dependència externa.
