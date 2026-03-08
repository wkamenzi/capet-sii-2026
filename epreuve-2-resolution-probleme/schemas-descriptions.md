# Épreuve 2 — Hydrolienne HydroFlux-V5 : Schémas et figures

> Ce fichier décrit toutes les figures du sujet d'épreuve 2. Pour chaque figure, une description textuelle détaillée et un schéma ASCII art sont fournis. Des indications d'illustration libre de droits sont données quand disponibles.

---

## Figure 1 — Vue de dessus de l'HydroFlux-V5 (turbine Darrieus)

### Description textuelle

Vue de dessus (coupe horizontale) de la turbine à axe vertical. Le rotor est composé de 3 pales profilées NACA 0018 disposées à 120° sur un cercle de rayon R = 1,0 m. L'arbre central est au centre. Les pales sont représentées avec leur profil aérodynamique. La direction du courant (vecteur V) est indiquée par une flèche. Le sens de rotation (sens antihoraire dans cette vue) est indiqué par une flèche courbe.

### Schéma ASCII art — Vue de dessus

```
    Vue de dessus — HydroFlux-V5
    Turbine Darrieus à 3 pales, axe vertical
    
    → → → V = 2,5 m/s (courant fluvial)
    
                    Pale 1 (à 0°)
                  ╔══════╗
                 ╔╝      ╚╗
                ╔╝  NACA   ╚╗
               ╔╝   0018    ╚╗
              ╔╝              ╚╗
             ╔╝                ╚════╗
             ╔══════════════════════╝
                           │ R = 1,0 m
    Pale 3      ──────────[●]──────────      Pale 2
    (à 240°)               │ Arbre          (à 120°)
                           │ central
    ╔═══════════╗          │          ╔═══════════╗
    ╚═╗         ╔═╗                ╔═╗         ╔═╝
       ╚═╗   ╔═╝                  ╚═╗   ╔═╝
          ╚═╝                          ╚═╝
    
    Sens de rotation : antihoraire (→ dans ce sens optimal avec courant →)
    
    ┌─────────────────────────────────────────────────────────────┐
    │  Caractéristiques :                                          │
    │  - Rayon R = 1,0 m                                           │
    │  - 3 pales NACA 0018, corde c ≈ 0,25 m                      │
    │  - Hauteur H = 1,5 m (axe vertical, hors plan de ce schéma)  │
    │  - Surface de capture S = D × H = 2,0 × 1,5 = 3,0 m²        │
    └─────────────────────────────────────────────────────────────┘
```

### Schéma ASCII art — Vue de profil (coupe verticale)

```
    Vue de profil — Plan sagittal (xz)
    
    z ↑ (axe vertical)          eau de surface (libre)
      │                         ────────────────────────
      │    ←──── 3 m (immersion minimale) ────→
      │
      │         ┌──────────────────────────────┐
      │         │  Pale 1 (vue de profil = tranche)
      │         │  ════════════════════════════
      │         │                              │  H = 1,5 m
      │         │  ════════════════════════════
      │         │  Pale coupe vue de profil    │
      │         └──────────────┬───────────────┘
      │                        │ Arbre central
      │                        │ Ø = 70 mm (acier 316L)
      │                        │
      │                   ┌────┴────┐
      │                   │ Boîtier │ Multiplicateur
      │                   │ GSAP    │ épicycloïdal
      │                   │ étanche │
      │                   └────┬────┘
      │                        │ Câble électrique
      │                   ┌────┴────┐
      │                   │ Ancrage │ Massif béton
      └───────────────────┴─────────┴────────────── fond du fleuve
                              →→→→→→ V (courant)
```

### Indications illustrations libres de droits

- Rechercher : "Darrieus turbine", "vertical axis water turbine" sur Wikimedia Commons
- Rechercher : "hydrokinetic turbine river" sur Google Images (filtrer par licence Creative Commons)
- Références commerciales (pour illustration uniquement) : HydroQuest, Guinard Energies, Sabella

---

## Figure 2 — Profil NACA 0018 d'une pale

### Description textuelle

Profil symétrique NACA 0018 (épaisseur relative 18 %). Le profil est représenté avec son bord d'attaque arrondi à gauche et son bord de fuite effilé à droite. L'angle d'attaque α est indiqué par rapport à la direction de l'écoulement relatif (vecteur vitesse relative de l'eau par rapport à la pale en rotation).

### Schéma ASCII art

```
    Profil NACA 0018 — Pale d'hydrolienne
    
    Vecteur vitesse relative : V_rel = V_courant - V_pale
    
    V_rel →          ← bord d'attaque
                    ╭──────────────────────────────────────────╮
    α → (angle      │                                          │→ bord de fuite
    d'attaque)      │    Profil NACA 0018                       │
                    │    (symétrique, e/c = 18 %)               │
                    ╰──────────────────────────────────────────╯
                    
                    ←──────── Corde c ≈ 0,25 m ────────────────→
                    
    Forces aérodynamiques :
    ↑ Portance L (perpendiculaire à V_rel)  → fait tourner le rotor
    ← Traînée D (parallèle à V_rel)         → perte d'énergie
    
    Coefficient de puissance Cp = f(λ, α_moyen) → maximum à λ = 2,5
```

---

## Figure 3 — Courbe Cp(λ) de la turbine Darrieus

### Description textuelle

Courbe de coefficient de puissance Cp en fonction du rapport de vitesse spécifique λ (TSR). La courbe a la forme d'une cloche avec un maximum Cp,max = 0,35 à λ_opt = 2,5. Elle monte progressivement de 0 (à λ = 0) vers le maximum, puis redescend vers 0 pour des λ élevés. La limite de Betz (Cp = 16/27 ≈ 0,593) est indiquée par une droite horizontale en pointillés.

### Schéma ASCII art

```
    Cp
    
    0,593 ┤ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─  Limite de Betz (16/27)
          │
    0,400 ┤
          │          ★ Cp,max = 0,35 (λ = 2,5)
    0,350 ┤        ╱   ╲
          │       ╱      ╲
    0,300 ┤      ╱         ╲
          │     ╱            ╲
    0,250 ┤    ╱               ╲
          │   ╱                  ╲
    0,200 ┤  ╱                     ╲
          │ ╱                        ╲
    0,150 ┤╱                           ╲
          │                              ╲
    0,100 ┤                                ╲
          │                                  ╲
    0,050 ┤                                    ╲
          │                                      ╲
    0,000 └──┬──┬──┬──┬──┬──┬──┬──┬──┬──┬──┬──── λ
             0  0,5  1  1,5  2  2,5  3  3,5  4
             
    Zone optimale : λ ∈ [2,0 ; 3,0] (région utile de fonctionnement)
    
    λ < λ_opt → décrochage aérodynamique des pales
    λ > λ_opt → sillage perturbé entre les 3 pales (interférence)
    
    À V_n = 2,5 m/s : λ_opt = 2,5 → n_opt = 59,7 tr/min (≤ 60 tr/min ✔)
```

---

## Figure 4 — Chaîne d'énergie de l'HydroFlux-V5

### Description textuelle

Schéma de la chaîne d'énergie depuis l'énergie cinétique de l'eau jusqu'au réseau électrique. Chaque étage est représenté par un bloc fonctionnel. Les rendements sont indiqués entre les blocs. Les puissances sont calculées à la vitesse nominale Vn = 2,5 m/s.

### Schéma ASCII art

```
    ┌─────────────────────────────────────────────────────────────────────────────┐
    │                    CHAÎNE D'ÉNERGIE — HydroFlux-V5                          │
    │                    Vitesse nominale : V_n = 2,5 m/s                          │
    └─────────────────────────────────────────────────────────────────────────────┘
    
    ┌──────────┐   Cp=0,35    ┌──────────┐  η=0,96    ┌──────────┐  η=0,90    ┌──────────┐
    │  EAU     │   ────────→  │ TURBINE  │  ────────→  │ MULTIPLI │  ────────→  │GÉNÉRATT. │  ────→ RÉSEAU
    │  P_hyd   │              │  ROTOR   │             │ CATEUR   │             │  GSAP    │
    │ 23,4 kW  │              │ 8,2 kW   │             │  7,9 kW  │             │  7,1 kW  │
    └──────────┘              └──────────┘             └──────────┘             └──────────┘
    
                    Pertes :              Pertes :               Pertes :
                    15,2 kW               0,3 kW                 0,8 kW
                    (sillage)             (frottement)           (chaleur)
                    
    ─────────────────────────────────────────────────────────────────────────────────
    
    BILAN : η_global = Cp × η_multi × η_gen = 0,35 × 0,96 × 0,90 = 0,302 = 30,2 %
    
    Énergie restituée au réseau : 7,1 kW
    Énergie cinétique disponible : 23,4 kW
    
    ┌────────────────────────────────────────┐
    │  Répartition des pertes :              │
    │  ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓ 64,9 % → sillage    │
    │  ▓▓ 1,3 % → multiplicateur            │
    │  ▓▓▓ 3,4 % → génératrice              │
    │  ████████████ 30,2 % → réseau (utile) │
    └────────────────────────────────────────┘
```

---

## Figure 5 — Diagramme de l'arbre en torsion (Phase 3)

### Description textuelle

Schéma de l'arbre central de la turbine soumis à la torsion. L'arbre est représenté en vue de profil et en coupe transversale. Le couple résistant C_turbine est appliqué par le rotor en haut de l'arbre, et le couple résistant de la génératrice (via le multiplicateur) est appliqué en bas. La contrainte de cisaillement τ est représentée sur la section transversale.

### Schéma ASCII art

```
    Arbre de turbine — Sollicitation en torsion
    
    Vue de profil :
    
           ← C_turbine = 1312 N·m (couple moteur du rotor)
    ┌──────┐
    │ Rotor│     ↻ (sens de rotation)
    └──┬───┘
       │
       │ ← Arbre cylindrique plein
       │    Ø = 70 mm (acier 316L)
       │    l = 1,8 m (entre paliers)
       │
    ┌──┴──────────┐
    │ Multiplicateur │ ← C_gen = C_turbine × η_multi (couple résistant)
    └─────────────┘
    
    Section transversale (coupe AA) :
    
         ╭─────────────╮
        ╭               ╮
       │    ↑ τ_max      │  τ_max = 16 × C / (π × d³)
       │ ←  d = 70 mm → │  τ_max à la surface (r = d/2)
       │                 │
        ╰               ╯
         ╰─────────────╯
         
         τ_max (en surface) → contrainte de cisaillement maximale
         τ = 0 (en centre) → contrainte nulle sur l'axe
         
         Distribution parabolique de τ sur le rayon :
         τ(r) = τ_max × (r / (d/2))
         
    Données de dimensionnement :
    ─────────────────────────────────
    Couple nominal    : C_nom = 1 312 N·m
    Couple en crue    : C_max = 3 360 N·m
    τ_adm (acier 316L): 63,5 MPa
    d_min calculé     : 64,6 mm
    d retenu          : 70 mm (série normalisée)
    Vérification      : τ_max (d=70mm, C=C_max) ≈ 56 MPa < τ_adm ✔
```

---

## Figure 6 — Site fluvial et installation de l'hydrolienne

### Description textuelle

Vue en plan (vue de dessus) du site de la Loire à Montjean-sur-Loire montrant le positionnement de l'hydrolienne dans le chenal. Vue en coupe transversale (perpendiculaire au courant) montrant la profondeur du fleuve et la position de la turbine immergée.

### Schéma ASCII art — Vue en plan

```
    Vue en plan du site — Loire à Montjean-sur-Loire
    
    Rive gauche
    ═══════════════════════════════════════════════════════════════════════
    
    → → → → → → → → V = 2,5 m/s (courant) → → → → → → → → → →
                        
                        ★ HydroFlux-V5                         
    → → → → → → → → →  (immergée à 3 m)  → → → → → → → → →    
                        
    ← 250 m (largeur chenal) →
    
    ═══════════════════════════════════════════════════════════════════════
    Rive droite
    
    Câble électrique sous-marin → Poste de livraison (rive)
    ══════════════════════════════════════════════════════════════════════
```

### Schéma ASCII art — Vue en coupe transversale

```
    Coupe transversale AA — Vue depuis l'aval
    
    z ↑ (vertical)
      │        
      │ 0,0 m  ────────────────────── Surface libre (eau) ───────────────────
      │                                          ↑
      │                              H = 1,5 m (pales)
      │ -1,5 m         ╔══════════════════╗      ↕
      │                ║  Rotor Darrieus  ║  ← 2R = 2,0 m →
      │                ║  (3 pales)       ║
      │ -3,0 m         ╚══════════════════╝     Profondeur min.
      │                        │                d'immersion = 3 m
      │                   ┌────┴──────┐
      │                   │ Boîtier   │
      │                   │ + GSAP    │
      │ -4,5 m            └─────────  ┘  ← fond du fleuve (profondeur moy. 4,5 m)
      │════════════════════════════════════════════════════════ fond
      
      Profil de vitesse :
      V(z) ≈ V_moy × (z/H_total)^(1/7)  (loi puissance 1/7)
      → Variation d'environ ±15 % sur la hauteur des pales
```

---

## Figure 7 — Distribution de Weibull et histogramme des vitesses

### Description textuelle

Histogramme représentant la durée annuelle (en heures) en fonction de la plage de vitesse du courant. Les barres représentent les 7 plages de vitesse du document DR-2. La courbe de Weibull théorique est superposée. La limite de vitesse minimale (V_min = 1,5 m/s) et la vitesse nominale (V_n = 2,5 m/s) sont marquées par des lignes verticales en pointillés.

### Schéma ASCII art

```
    Histogramme des durées annuelles — Site Loire Montjean
    
    Δt (h/an)
    
    1800 │      ██████████████████ (1752 h)  ██████████████████ (1752 h)
         │      ██  [1,5-2,0 m/s]  ██        ██  [2,0-2,5 m/s]  ██
    1400 │      ████████████████████████       ██████████████████████
         │  ██  ██████████████████████████      █████████████████████  ██
    1000 │  ██  ██████████████████████████      █████████████████████  ██
         │  ██  ██████████████████████████      █████████████████████  ██
     800 │  ██  ██████████████████████████      █████████████████████  ██
         │  ██  ██████████████████████████      █████████████████████  ██
         │  ██  ██████████████████████████      █████████████████████  ██
         │
       0 └──┬──────────┬──────────┬──────────┬──────────┬──────────┬── V (m/s)
            0   0,5    1,0        1,5         2,0        2,5        3,0
            
                               ↑                       ↑
                          V_min = 1,5                V_n = 2,5
                        (démarrage turbine)        (puissance nominale)
    
    ─────────────────────────────────────────────────────────────────────
    Durées clés :
    - Turbine à l'arrêt (V < 1,5 m/s) : 876 + 1314 = 2190 h/an (25 %)
    - En fonctionnement (V ≥ 1,5 m/s) : 6570 h/an (75 %)
    - À puissance nominale (V ≥ 2,5 m/s) : 3066 h/an (35 %)
```

---

## Figure 8 — Diagramme P_hyd(V) — Puissance hydraulique en fonction de la vitesse

### Description textuelle

Courbe de puissance hydraulique disponible P_hyd(V) = 1500 × V³ (en W) en fonction de la vitesse du courant V (en m/s). La courbe est une parabole cubique. Les points correspondant aux vitesses nominale et de crue sont repérés. La puissance électrique réelle P_élec(V) = η_global × P_hyd(V) est représentée en second.

### Schéma ASCII art

```
    P (kW)
    
    100 ┤                                          ★ P_hyd (crue V=4,0 m/s) = 96 kW
        │
     80 ┤                                       ╱
        │                                   ╱
     60 ┤                               ╱
        │                           ╱
     40 ┤                       ╱     ◈ P_hyd = 64 kW (V=3,5 m/s)
        │                   ╱
     23 ┤               ◆ P_hyd (V=2,5 m/s) = 23,4 kW   ← Puissance hydraulique P_hyd(V) = 1500×V³
        │           ╱
     10 ┤       ╱           ◇ P_élec (V=2,5) = 7,1 kW    ← Puissance électrique P_élec(V) = η×P_hyd
      5 ┤   ╱                                                (η_global = 0,302)
        │ ╱      ↑ P_n = 5 kW plafond de régulation
      0 └──────────────────────────────────────────── V (m/s)
        0  0,5  1,0  1,5  2,0  2,5  3,0  3,5  4,0
        
              ↑             ↑              ↑
           V_min         V_n          V_survie
          (1,5 m/s)    (2,5 m/s)     (4,0 m/s)
          
    Zone de fonctionnement effectif : [1,5 ; 4,0] m/s
    Zone de régulation (puissance plafonnée à 5 kW) : [2,4 ; 4,0] m/s
```

---

## Figure 9 — Schéma de principe du multiplicateur épicycloïdal

### Description textuelle

Schéma de principe d'un train épicycloïdal à un étage. Le planétaire (solaire) est en sortie (côté génératrice), la couronne est fixe (liée au carter), et le porte-satellites est en entrée (côté turbine). Le rapport de multiplication est μ = 1 + Z_couronne/Z_planétaire.

### Schéma ASCII art

```
    Multiplicateur épicycloïdal — Schéma de principe
    
    Vue de face (coupe transversale) :
    
                    ╔════════════════════╗  ← Couronne (fixe, liée au carter)
                   ╔╝                   ╚╗    Z_couronne ≈ 75 dents
                  ╔╝    ╔═══════╗        ╚╗
                 ╔╝     ║       ║         ╚╗
         Satellite→  ┌─[●]─┐   ║Planétaire║ ← Arbre de sortie (→ génératrice)
               ╔╝    │     │   ║  Z_plan  ║╚╗   n_gen = n_turb × μ
              ╔╝     └─────┘   ╚═════╤════╝ ╚╗
              ║ Z_sat ≈ 25    [●]── Axe      ║
              ║               porte-sat ──╗  ║
              ╚╗          ╔═════╗         ║ ╔╝
               ╚╗         ║     ║  ┌─────┘╔╝
                ╚╗    Satellite  ║  │     ╔╝
                 ╚╗         ╚═════╝╔╝    ╔╝
                  ╚╗              ╔╝    ╔╝
                   ╚╗            ╔╝    ╔╝
                    ╚════════════╝
    
    Arbre d'entrée (← turbine) : n_turb ≈ 60 tr/min (porte-satellites)
    
    ─────────────────────────────────────────────────────────────────
    Calcul du rapport :
    
    μ = 1 + Z_couronne/Z_planétaire
    Avec μ = 12,6 et Z_couronne/Z_planétaire ≈ 11,6
    → Exemple : Z_planétaire = 13 dents, Z_satellite = 26, Z_couronne = 65
    
    Vérification : μ = 1 + 65/13 = 1 + 5 = 6  (un seul étage)
    → Pour μ = 12,6 : deux étages nécessaires (μ₁ × μ₂ = 12,6)
       Étage 1 : μ₁ = 3,5 ; Étage 2 : μ₂ = 3,6
       Rendement combiné : η = 0,98 × 0,98 ≈ 0,96 ✔
```

---

## Indications générales pour les candidats

### Recherche d'illustrations libres de droits

| Figure | Mots-clés de recherche | Sources recommandées |
|---|---|---|
| Turbine Darrieus | "Darrieus wind turbine diagram", "VAWT schematic" | Wikimedia Commons (nombreux schémas SVG libres) |
| Profil NACA | "NACA airfoil", "NACA 0018 cross section" | Wikimedia Commons, UIUC Airfoil Coordinates Database |
| Site fluvial Loire | "Loire fleuve aérien", "Loire vu du ciel" | IGN Géoportail (ortho libre), Google Earth |
| Distribution Weibull | "Weibull distribution wind energy" | Wikimedia Commons |
| Arbre en torsion | "shaft torsion stress distribution" | Livres de RDM en open access |
| Multiplicateur épicycloïdal | "planetary gear train diagram", "epicyclic gearbox" | Wikimedia Commons |

### Logiciels de création de schémas

- **FreeCAD** (libre) : modélisation 3D, coupes, schémas cinématiques
- **Inkscape** (libre) : figures vectorielles, profils NACA, schémas hydrauliques
- **Gnuplot** (libre) : courbes Cp(λ), P_hyd(V), histogrammes
- **GeoGebra** (libre) : géométrie du rotor Darrieus, angles d'attaque
- **LibreOffice Calc + Chart** (libre) : histogramme des vitesses, bilan énergétique
