# Épreuve 1 — Exosquelette EXOARM-S3 : Schémas et figures

> Ce fichier décrit toutes les figures du sujet d'épreuve 1. Pour chaque figure, une description textuelle détaillée et un schéma ASCII art sont fournis. Des indications d'illustration libre de droits sont données quand disponibles.

---

## Figure 1 — Vue générale de l'EXOARM-S3

### Description textuelle

Vue de trois-quarts arrière d'un opérateur vêtu d'un bleu de travail portant l'exosquelette EXOARM-S3. L'exosquelette ressemble à un sac à dos allégé avec deux bras articulés métalliques déployés latéralement. Les bras articulés s'étendent depuis le châssis dorsal jusqu'aux avant-bras de l'opérateur, maintenus par des manchons rembourrés. Des ressorts à gaz chromés sont visibles entre les articulations. L'ensemble est de couleur anthracite avec des inserts orange fluorescent pour la visibilité en atelier.

### Schéma ASCII art — Vue de face (plan frontal)

```
           ╔══════════════════╗
           ║  EXOARM-S3       ║
           ║  Vue de face     ║
           ╚══════════════════╝

              ┌─────────┐
              │  Tête   │
              └────┬────┘
        ┌──────────┼──────────┐
        │     Épaule G.       │ Épaule D.
   ┌────┤    ╔═══════════╗    ├────┐
  [Pivot]   ║   Châssis  ║   [Pivot]
 S0/S1 G.  ║   dorsal   ║  S0/S1 D.
        │   ╚═══════════╝   │
        │        S0          │
  S1 G. │                   │ S1 D.
   ┌────┤                   ├────┐
  [Pivot]                  [Pivot]
 S1/S2 G.                 S1/S2 D.
        │                   │
  S2 G. │                   │ S2 D.
   (bras│                   │bras)
  articu│lé                 │articulé
        │                   │
   [╔═══╧═══╗]         [╔═══╧═══╗]
   ║ Manchon║           ║Manchon║
   ║ bras G.║           ║bras D.║
   ╚════════╝           ╚════════╝
        S3 G.                S3 D.

Ressort à gaz R1 : relie S0 (point A bas)
à S2 (point B haut) — visible latéralement
```

### Schéma ASCII art — Vue de côté (plan sagittal droit)

```
           z ↑
             │
    S0       │     Δ₁ (axe pivot épaule)
  ╔══════╗   │    ╱
  ║Châssis╠──┼──[●]──────── S1 (attelle, L₁ = 0,18 m)
  ║dorsal ║  │              │
  ╚══════╝   │    Δ₂ (axe pivot bras)
             │              │
             │           [●]──── S2 (bras articulé, L₂ = 0,32 m)
             │              │                        │
             │              │     R1 (ressort à gaz) │
             │         A [○]┤    ╱╲ ╱╲ ╱╲           │
             │              │   ╱  ╳  ╳  ╲          │
             │              │  ╱            ╲        │
             │              └────────────[○] B       │
             │                                       │
             │                              ╔════════╧╗
             │                              ║  Manchon ║
             │                              ║  bras S3 ║
             └──────────────────────────────╚══════════╝
                                                      → x

    Angle θ₁ = angle de S1/S0 par rapport à la verticale z
    Position repos (bras le long du corps) : θ₁ = 0°
    Position horizontale (bras à l'horizontale) : θ₁ = 90°
```

### Indications illustrations libres de droits

- Rechercher : "exoskeleton upper limb industrial" sur Wikimedia Commons
- Rechercher : "MATE exoskeleton" ou "industrial wearable robot" sur Pixabay (licence CC0)
- Référence commerciale (pour illustration uniquement) : Comau MATE-XT, Exhauss Exovest, Levitate AIRFRAME

---

## Figure 2 — Diagramme pieuvre de l'EXOARM-S3

### Description textuelle

Diagramme pieuvre standard (octopus diagram) centré sur le produit EXOARM-S3. Le produit est représenté par un ovale central. Les éléments du milieu extérieur sont disposés en cercle autour du produit, reliés par des traits représentant les fonctions de service.

### Schéma ASCII art

```
                    ┌──────────────┐
                    │  Opérateur   │
                    └──────┬───────┘
                           │ FP
              ┌─────────── │ ─────────────┐
              │            │              │
   ┌──────────┴──┐   ╔═════╧══════╗  ┌───┴──────────┐
   │    Outil    │   ║            ║  │  Env. travail │
   │  industriel │FP ║  EXOARM-S3 ║FC│  (espace,     │
   └─────────────┘   ║            ║  │   obstacles)  │
                     ╚═════╤══════╝  └───────────────┘
              │            │              │
   ┌──────────┴──┐         │FC     ┌──────┴──────────┐
   │  Norme      │         │       │     Énergie      │
   │ EN ISO 13482│        FC│       │  (ressorts,     │
   └─────────────┘    ┌────┴────┐  │   précontrainte)│
                      │Réseau de│  └─────────────────┘
                      │mainten. │
                      └─────────┘

    FP = Fonction Principale
    FC = Fonction Contrainte
    
    FP : EXOARM-S3 permet à l'Opérateur d'assister son travail
         avec l'Outil industriel
    FC₁ : EXOARM-S3 doit respecter la Norme EN ISO 13482
    FC₂ : EXOARM-S3 doit pouvoir être entretenu par le Réseau maintenance
    FC₃ : EXOARM-S3 doit ne pas gêner dans l'Env. de travail
    FC₄ : EXOARM-S3 stocke et restitue l'Énergie des ressorts
```

---

## Figure 3 — Schéma cinématique de la chaîne articulée

### Description textuelle

Schéma cinématique dans le plan sagittal (vue de côté) représentant la chaîne articulée droite de l'exosquelette. Le schéma utilise les conventions normalisées : liaisons pivot représentées par des cercles, encastrement par des hachures, ressort par un zigzag. Les solides sont schématisés par des barres pleines ou des formes géométriques simples.

### Schéma ASCII art — Conventions cinématiques

```
    z ↑                     LÉGENDE :
      │              [●] Pivot (axe perpendiculaire au plan)
      │              ═══ Encastrement (hachures)
      │              ╱╲╱╲ Ressort (à gaz ou hélicoïdal)
      │              ─── Solide rigide (barre)
      │
      │  S0 (bâti/châssis dorsal)
  ════╪════ ◄── Encastrement S0/sol (bâti)
      │
  [●] Δ₁ ─────────────────────────────── S1 (L₁ = 0,18 m)
  (Pivot, axe z)                          │
      │  A [○]────╲                   [●] Δ₂ ───────────────── S2 (L₂ = 0,32 m)
      │        ╲   ╲  R1               (Pivot, axe z)               │
      │         ╲   ╲ (ressort à gaz                          [══════╧══════]
      │          ╲   ╲  ╱╲ ╱╲ ╱╲                             Encastrement S2/S3
      │           ╲    ╲╱  ╲╱  ╲╱                                   │
      │            ╲                                          S3 (manchon)
      │             ╲──────────── [○] B (pivot sphérique sur S2)
      │                           (d₂ = 0,10 m de Δ₂)
      │
      └──────────────────────────────────────────────────── x

    Paramètre cinématique : θ₁ (angle S1/S0), θ₂ = 0,5 × θ₁ (imposé par câble)
    L'angle θ_eff de l'effecteur S3 = θ₁ + θ₂ = 1,5 × θ₁
```

---

## Figure 4 — Schéma PFS (Principe Fondamental de la Statique) — Partie C

### Description textuelle

Vue de côté du système isolé {S2 + bras opérateur + outil} en position bras horizontal (θ₁ = 90°). Tous les vecteurs forces sont représentés avec leurs points d'application, leurs directions et leurs sens. La liaison en Δ₁ est représentée par ses composantes de réaction.

### Schéma ASCII art

```
    z ↑         Bilan des forces sur {S2 + bras opérateur + outil}
      │         Position : θ₁ = 90° (bras horizontal)
      │
      │    Δ₁                    G₂              G_bras         Outil
  ────●────┬──────────────────────●────────────────●──────────────●──── x
      │    │← L₁/2 = 0,08 m →│← 0,16 m →│    │← 0,30 m →│    │← 0,60 m →│
      │    │                   │           │               │               │
  R_z ↑   │                   ↓           ↓               ↓               ↓
  R_x →   │                  P_S2        P_bras          P_outil
  (réaction│              = 4,41 N     = 39,24 N        = 19,62 N
   en Δ₁) │
      │    │
      │    B [○] Point d'application du ressort R1
      │        ↗ F_R1 (à 40° au-dessus de l'horizontale)
      │       α = 40°
      │
    Note : les moments par rapport à Δ₁ :
    - P_S2 crée un moment résistant (sens horaire) : M_S2 = -4,41 × 0,16 = -0,71 N·m
    - P_bras crée un moment résistant : M_bras = -39,24 × 0,30 = -11,77 N·m
    - P_outil crée un moment résistant : M_outil = -19,62 × 0,60 = -11,77 N·m
    - F_R1 (composante verticale) crée un moment moteur : M_R1 = F_R1 × sin(40°) × d₂
```

---

## Figure 5 — Poutre encastrée-libre (Partie D)

### Description textuelle

Vue de côté de la barre de support dorsale modélisée comme une poutre encastrée-libre. L'encastrement est à gauche (point A), l'extrémité libre est à droite (point B). La force F est appliquée verticalement vers le bas en B. La section transversale du profilé rectangulaire creux est représentée en coupe à droite.

### Schéma ASCII art

```
    POUTRE ENCASTRÉE-LIBRE — Barre de support dorsale

    A (encastrement)            B (extrémité libre)
    ╔═══╗════════════════════════════════════●
    ╠═══╣◄──────────── L = 0,40 m ─────────►↓
    ╚═══╝                                    F = 85 N
    (hachures)
    
    Section rectangulaire creuse (coupe transversale) :
    
         b = 30 mm
    ┌────────────────────────────┐
    │  ┌──────────────────────┐  │← e = 2 mm
    │  │                      │  │
    │  │  Section creuse      │  │ h = 20 mm
    │  │  (b-2e)×(h-2e)       │  │
    │  │  = 26 × 16 mm        │  │
    │  └──────────────────────┘  │← e = 2 mm
    └────────────────────────────┘
    
    Izz = 11 125 mm⁴ (voir calcul Partie D, Q D11.b)
```

### Schéma ASCII art — Diagrammes des efforts intérieurs

```
    Diagramme de l'effort tranchant T(x) [N] :
    
     85 ┤████████████████████████████████████████
        │
      0 └────────────────────────────────────── x
        A (x=0)                              B (x=L)
        
    → T(x) = F = 85 N = constant sur toute la longueur
    
    ─────────────────────────────────────────────────────
    
    Diagramme du moment fléchissant Mf(x) [N·m] :
    
      0  ┐                                   /
         │                              /
    -17  │                        /
         │                   /
    -34  ╘══════════════/
         A (x=0)                              B (x=L)
         Mf(0) = -34 N·m                      Mf(L) = 0
         
    → Mf(x) = -F(L-x) = -85(0,40-x) : droite de pente +85 N
    → Moment maximal |Mf,max| = 34 N·m en x=0 (encastrement)
    → La fibre tendue est la fibre supérieure (z = +h/2 = +10 mm)
```

---

## Figure 6 — Diagramme d'Ashby — Partie D, Q14

### Description textuelle

Diagramme d'Ashby représentant le module de Young E (GPa) en abscisse et la masse volumique ρ (kg/m³) en ordonnée, sur des axes logarithmiques. Les matériaux sont représentés par des ellipses de différentes couleurs. Les lignes de performance (E/ρ = constante, E^(1/2)/ρ = constante) permettent de comparer les matériaux pour différentes applications.

### Schéma ASCII art simplifié

```
    Diagramme d'Ashby : Module de Young E vs Masse volumique ρ
    (axes logarithmiques)
    
    ρ (kg/m³)
    10000 │                          Aciers
          │                       ╔═══════╗
          │                       ║  Fe   ║
          │                       ╚═══════╝
     5000 │          Titane   ╔══════════╗
          │         ╔══════╗  ║ Alliages ║
          │         ║  Ti  ║  ║  d'acier ║
          │         ╚══════╝  ╚══════════╝
     3000 │  ╔════════════╗
          │  ║ Aluminium  ║◄── 7075-T6 (E=71, ρ=2810)
     2000 │  ║  alliages  ║
          │  ╚════════════╝
     1500 │           ╔═══════════════════╗
          │           ║ Composite C/époxy ║◄── UD (E=135, ρ=1550)
     1000 │           ╚═══════════════════╝
          │
          └──────────────────────────────── E (GPa)
              1      10     100    500
    
    Droite de performance rigidité/masse (poutres en flexion) :
    → E^(1/2)/ρ = constante
    
    Composite C/époxy : E^(1/2)/ρ = √135/1550 = 11,62/1550 = 7,50 × 10⁻³
    Aluminium 7075    : E^(1/2)/ρ = √71/2810  =  8,43/2810 = 3,00 × 10⁻³
    
    → Le composite est 2,5 fois plus performant que l'aluminium pour
      une poutre en flexion à masse égale.
```

---

## Figure 7 — Diagramme cinématique d'entrée-sortie (Partie B)

### Description textuelle

Graphe θ_eff en fonction de θ₁, montrant la relation linéaire θ_eff = 1,5 × θ₁. L'axe des abscisses représente l'angle d'entrée θ₁ de 0° à 150°, l'axe des ordonnées représente l'angle de sortie θ_eff de 0° à 225°.

### Schéma ASCII art

```
    θ_eff (°)
    
     225 │                              ★ (150°, 225°)
         │                          ╱
     180 │                      ╱
         │                  ╱
     135 │              ╱       ← θ_eff = 1,5 × θ₁
         │          ╱           (loi linéaire, pente 1,5)
      90 │      ╱
         │  ╱
       0 └──────────────────────────── θ₁ (°)
         0  30  60  90  120  150
         
    Points remarquables :
    ─────────────────────────────────
    θ₁ = 0°    →  θ_eff = 0°
    θ₁ = 60°   →  θ_eff = 90°   (bras à l'horizontale quand épaule à 60°)
    θ₁ = 90°   →  θ_eff = 135°
    θ₁ = 120°  →  θ_eff = 180°  (bras vertical au-dessus de la tête)
    θ₁ = 150°  →  θ_eff = 225°
```

---

## Figure 8 — Chaîne d'information (version active motorisée)

### Description textuelle

Schéma bloc de la chaîne d'information pour la version active de l'exosquelette. Les blocs représentent les composants fonctionnels de la chaîne de commande, reliés par des flèches montrant le sens du flux d'information.

### Schéma ASCII art

```
    ┌─────────────────────────────────────────────────────────────────────┐
    │                   CHAÎNE D'INFORMATION — EXOARM actif               │
    └─────────────────────────────────────────────────────────────────────┘
    
    Consigne                                              Effet physique
    (intention ──→ [CAPTEUR EMG] ──→ [TRAITEMENT] ──→ [ACTIONNEUR] ──→  sur le
     de mouvement)  (déltoïde)      (µcontroleur)    (moteur BLDC)      membre
    
                        ↑ Signal          ↑ Commande PWM
                        │ analogique       │ 0-24V
                        │ filtré           │
                   ┌────┴─────────────────┴────┐
                   │   Conditionnement signal   │
                   │   + conversion CAN (12 bits)│
                   └────────────────────────────┘
    
    ← ← ← ← ← ← ← ← ← BOUCLE DE RETOUR ← ← ← ← ← ← ← ← ← ← ← ←
                    [Codeur incrémental Δ₁, 1024 pts/tour]
                           (mesure θ₁ et θ̇₁)
    
    COMPOSANTS :
    ├─ Capteur : électrodes EMG surface (type DELSYS Trigno)
    ├─ Traitement : STM32F4 + filtre passe-bas Butterworth 20 Hz
    ├─ Actionneur : moteur BLDC 24V, 150W, couple max 8 N·m
    └─ Retour : codeur incrémental 1024 pts/tour + conversion angulaire
```

---

## Figure 9 — Modèle dynamique du bras (Partie E)

### Description textuelle

Schéma du modèle dynamique simplifié représentant le système {bras + outil + S2} comme un solide en rotation autour de l'axe Δ₁. Les couples intervenants (gravitaire, ressort, musculaire, amortissement) sont représentés par des flèches courbées autour de l'axe de rotation.

### Schéma ASCII art

```
    Modèle dynamique — Rotation autour de Δ₁
    
                    z ↑
                      │
           Δ₁ ────────●──────────────────────────→ x
                       ╲         │               │       │
               θ₁↗      ╲        │               │       │
                          ╲      ↓               ↓       ↓
                           ╲   G_S2           G_bras  Outil
                            ╲  P_S2           P_bras  P_outil
                             ╲
              
    COUPLES APPLIQUÉS autour de Δ₁ :
    
    ┌─────────────────────────────────────────────────────────────────┐
    │  C_grav(θ₁) = (m_bras × l_G + m_outil × l_outil) × g × cos(θ₁)│
    │               → Résistant (s'oppose au levée du bras)           │
    │                                                                 │
    │  C_ressort   = F_R1 × sin(α(θ₁)) × d₂ ≈ 25 N·m (constant)     │
    │               → Moteur (aide au levée du bras)                  │
    │                                                                 │
    │  C_musc      = couple musculaire des deltoïdes                  │
    │               → Moteur (généré par l'opérateur)                 │
    │                                                                 │
    │  C_amort     = b × θ̇₁ = 0,8 × θ̇₁                              │
    │               → Résistant (dissipation aux articulations)       │
    └─────────────────────────────────────────────────────────────────┘
    
    PFD : J × θ̈₁ = C_ressort + C_musc - C_grav(θ₁) - C_amort
    avec J = 0,75 kg·m²
```

---

## Indications générales pour les candidats

### Recherche d'illustrations libres de droits

Pour illustrer les sujets lors d'une présentation ou d'une publication pédagogique :

| Figure | Mots-clés de recherche | Sources recommandées |
|---|---|---|
| Exosquelette industriel | "industrial exoskeleton upper limb", "wearable robot industry" | Wikimedia Commons, Pixabay |
| TMS industrie | "musculoskeletal disorder factory", "ergonomics automobile assembly" | INRS (inrs.fr), EU-OSHA |
| Schéma cinématique | "kinematic diagram shoulder mechanism" | Publications IEEE Robotics |
| Diagramme d'Ashby | "Ashby chart materials selection" | CES EduPack, Granta Design |
| Ressort à gaz | "gas spring technical drawing" | Stabilus, Bansbach (catalogues libres) |

### Logiciels de création de schémas

- **FreeCAD** (libre) : schémas cinématiques 2D/3D
- **LibreOffice Draw** (libre) : diagrammes pieuvre, schémas blocs
- **Inkscape** (libre) : figures vectorielles, schémas ASCII améliorés
- **GeoGebra** (libre) : graphes de lois entrée-sortie, diagrammes
