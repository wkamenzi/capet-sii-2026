# CAPET SII — Ingénierie Mécanique — Session 2026
## Épreuve 1 : Modélisation d'un produit — **CORRIGÉ DÉTAILLÉ**

---

> **Document d'entraînement non officiel — Usage pédagogique exclusivement**

---

## PARTIE A — Analyse fonctionnelle et cahier des charges

---

### Corrigé A1 — Diagramme pieuvre

#### Q A1.a — Fonction principale (FP)

**FP** : Permettre à l'**opérateur** de réduire son effort musculaire lors de tâches industrielles bras levés, en interagissant avec l'**outil industriel**.

*Reformulation possible* : "Permettre à l'opérateur d'effectuer des tâches répétitives en élévation de bras en réduisant la charge musculaire sur l'articulation de l'épaule."

#### Q A1.b — Fonctions contraintes (FC)

| Fonction | Justification |
|---|---|
| **FC1** : Ne pas gêner la mobilité naturelle de l'opérateur | L'exosquelette ne doit pas restreindre les mouvements hors zone de travail (marche, bras le long du corps) |
| **FC2** : Résister aux conditions d'environnement industriel | Présence de vibrations, poussières, produits chimiques, projections → matériaux résistants, étanchéité IP5X minimum |
| **FC3** : Respecter les normes de sécurité EN ISO 13482 | Obligation réglementaire pour les robots de service en contact avec l'opérateur |
| **FC4** : Être maintenu et réparé facilement (réseau de maintenance) | Les ressorts à gaz doivent être remplaçables sur site sans outillage spécial |

---

### Corrigé A2 — Diagramme des exigences SysML

#### Q A2.a — Complétion du tableau

| Case | Réponse | Justification |
|---|---|---|
| **[1]** | 30 % à 50 % (selon la charge) | Donné dans les caractéristiques constructeur — valeur cible à mi-charge : 40 % |
| **[2]** | ± 5 mm (réglage continu) | La taille varie continûment dans la plage 1,60–1,95 m ; un réglage par crans de 5 mm est raisonnable |
| **[3]** | Être léger et discret (ne pas surcharger l'opérateur) | Exigence implicite : l'exosquelette doit ajouter un minimum de masse portée |
| **[4]** | 2 millions de cycles | Donné dans les données constructeur |

#### Q A2.b — FP vs FC

| Exigence | Classification |
|---|---|
| EX-01 (réduire effort) | **Fonction principale** — c'est l'objectif premier du produit |
| EX-02 (adapter morphologie) | **Fonction contrainte** — condition de satisfaction de la FP |
| EX-03 (ne pas gêner) | **Fonction contrainte** — condition de sécurité et d'acceptabilité |
| EX-04 (être léger) | **Fonction contrainte** — contrainte sur la conception |
| EX-05 (durée de vie) | **Fonction contrainte** — exigence de fiabilité |
| EX-06 (norme) | **Fonction contrainte** — exigence réglementaire |

#### Q A2.c — Exigence supplémentaire (exemple)

| ID | Exigence | Critère | Niveau | Flexibilité |
|---|---|---|---|---|
| EX-07 | Être hygiénique et lavable | Résistance au nettoyage industriel (solvants, haute pression) | Certification IP65 | Non négociable |

*Autre exemple acceptable* : EX-08 — Être silencieux (bruit < 60 dB à 1 m de l'opérateur, car l'exosquelette ne doit pas perturber la communication en atelier).

---

### Corrigé A3 — Chaîne d'énergie et chaîne d'information

#### Q A3.a — Chaîne d'énergie complétée

```
┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐
│ Énergie stockée  │   │  [A] TRANSMETTRE │   │  [B] ADAPTER    │   │  [C] CONVERTIR  │
│ dans les ressorts│ → │  Tige du ressort │ → │  Levier S1-S2   │ → │  Rotation S2    │ → Réduction effort
│ à gaz (énergie   │   │  à gaz (guidage  │   │  (bras de levier│   │  → effort sur   │   musculaire
│ potentielle élast│   │  en translation) │   │  mécanique)     │   │  bras opérateur)│
└──────────────────┘   └──────────────────┘   └──────────────────┘   └──────────────────┘
```

| Bloc | Nom fonctionnel | Élément physique |
|---|---|---|
| **[A]** | Transmettre | Tige et corps du ressort à gaz R1 (transmission de la force axiale) |
| **[B]** | Adapter | Levier articulé S1–S2 (transformation du bras de levier) |
| **[C]** | Convertir | Articulation $\Delta_1$ (conversion force linéaire → couple en rotation) |

#### Q A3.b — Chaîne d'information (version active)

```
┌──────────────┐    ┌───────────────┐    ┌───────────────┐    ┌──────────────────┐
│   CAPTEUR    │    │  TRAITEMENT   │    │  ACTIONNEUR   │    │    EFFET SUR     │
│  EMG (signal │ →  │  Microcontrô- │ →  │  Moteur       │ →  │  le membre       │
│  musculaire  │    │  leur + algo  │    │  brushless    │    │  supérieur       │
│  à l'épaule) │    │  de commande  │    │  (couple de   │    │  (assistance     │
└──────┬───────┘    └───────────────┘    │  sortie)      │    │  en temps réel)  │
       │                                 └───────────────┘    └──────────────────┘
       │            ← Boucle de retour: capteur de position angulaire (codeur incrémental) ←
```

- **Capteur** : électrodes de surface EMG mesurant l'activité du muscle deltoïde
- **Traitement** : microcontrôleur STM32 + algorithme de détection d'intention (seuillage + filtrage passe-bas 20 Hz)
- **Actionneur** : moteur brushless BLDC 24 V, 150 W
- **Retour** : codeur incrémental sur axe $\Delta_1$ (1024 points/tour)

---

## PARTIE B — Modélisation cinématique

---

### Corrigé B4 — Schéma cinématique

```
        z (vertical)
        ↑
        │                    S3 (manchon bras)
        │              ╔════════════════════╗
        │              ║  Encastrement (S2→S3)
        │    Δ₂        ╚════════════════════╝
S0 ─── [●]────────────[●] Δ₂
(châssis   Pivot z     │   \
 dorsal)               │    S2 (bras articulé)
        │    Δ₁       [●] Δ₁
S0 ─── [●]────────────/
        │   Pivot z  S1 (attelle)
        │
    ┌───┴───────────────[○] A (pivot sphérique)
    │   Pivot sphérique  │
    │                    │ R1
    │                   ╱╲ (ressort à gaz)
    │                  ╱  ╲
    └──────────────[○] B (pivot sphérique sur S2)
```

**Récapitulatif des liaisons** :

| Liaison | Solides liés | Nature | Axe |
|---|---|---|---|
| L1 | S0 / S1 | Pivot | $\Delta_1$ (axe $z$ horizontal) |
| L2 | S1 / S2 | Pivot | $\Delta_2$ (axe $z$ parallèle à $\Delta_1$) |
| L3 | S2 / S3 | Encastrement | — |
| L4 | S0 / R1 | Pivot (point A) | Axe $y$ (dans le plan sagittal) |
| L5 | R1 / S2 | Pivot (point B) | Axe $y$ (dans le plan sagittal) |

---

### Corrigé B5 — Mobilité (formule de Grübler)

#### Q B5.a — Recensement des liaisons (en 2D, plan sagittal)

| Liaison | Pièces | Nature 2D | Mobilité $m_i$ | Contraintes $c_i = 3 - m_i$ |
|---|---|---|---|---|
| L1 (S0/S1) | Pivot d'axe $z$ | Pivot plan | 1 | 2 |
| L2 (S1/S2) | Pivot d'axe $z$ | Pivot plan | 1 | 2 |
| L3 (S2/S3) | Encastrement | Encastrement plan | 0 | 3 |
| L4 (S0/R1) | Sphérique en A | Pivot plan | 1 | 2 |
| L5 (R1/S2) | Sphérique en B | Pivot plan | 1 | 2 |

#### Q B5.b — Application de la formule de Grübler (2D)

Nombre de pièces (classes d'équivalence, bâti inclus) : $n = 5$ (S0, S1, S2, S3, R1)

$$M = 3(n - 1) - \sum c_i = 3(5 - 1) - (2 + 2 + 3 + 2 + 2)$$

$$\boxed{M = 12 - 11 = 1}$$

**Interprétation** : Le mécanisme possède **1 degré de mobilité**, ce qui est cohérent avec la conception. L'angle $\theta_1$ est le seul paramètre libre : quand l'épaule tourne, tous les autres solides sont contraints en conséquence. Le ressort R1 est un composant statiquement déterminé dans cette modélisation.

---

### Corrigé B6 — Loi entrée-sortie

#### Q B6.a — Relation entre angles

Par composition des rotations dans la chaîne ouverte S0 → S1 → S2 → S3 :

$$\theta_\text{eff} = \theta_1 + \theta_2$$

où $\theta_1$ est l'angle de S1/S0 et $\theta_2$ est l'angle de S2/S1 (angle relatif entre S2 et S1).

#### Q B6.b — Loi entrée-sortie

Avec $\theta_2 = k \cdot \theta_1 = 0{,}5 \cdot \theta_1$ :

$$\theta_\text{eff} = \theta_1 + 0{,}5 \cdot \theta_1$$

$$\boxed{\theta_\text{eff} = 1{,}5 \cdot \theta_1}$$

#### Q B6.c — Tableau de valeurs

| $\theta_1$ (°) | $\theta_\text{eff} = 1{,}5 \times \theta_1$ (°) |
|---|---|
| 0 | 0 |
| 60 | 90 |
| 90 | 135 |
| 120 | 180 |
| 150 | 225 |

#### Q B6.d — Allure et nature de la loi

La loi $\theta_\text{eff} = 1{,}5 \cdot \theta_1$ est une **fonction linéaire** (proportionnelle) : le graphe est une droite passant par l'origine, de pente $k_\text{total} = 1{,}5$.

```
θ_eff
(°)
 225 │                              *
     │                          *
 180 │                      *
     │                  *
 135 │              *
     │          *
  90 │      *
     │  *
   0 └──────────────────────────── θ₁ (°)
     0   30   60   90  120  150
```

Cette loi linéaire est caractéristique d'une **transmission par engrenages ou par câble-poulie à rapport constant**.

---

### Corrigé B7 — Vérification de l'amplitude articulaire

#### Q B7.a — Amplitude requise

Le cahier des charges (exigence EX-03) et la description système précisent : amplitude de flexion d'épaule de **0° à 150°**.

#### Q B7.b — Course effective du ressort

Données : $d_0 = 0{,}12 \, \text{m}$, $d_2 = 0{,}10 \, \text{m}$, $\phi_0 = 30°$

**Pour $\theta_1 = 0°$** :
$$L(0°) = \sqrt{d_0^2 + d_2^2 - 2 d_0 d_2 \cos(0° + 30°)}$$
$$= \sqrt{0{,}12^2 + 0{,}10^2 - 2 \times 0{,}12 \times 0{,}10 \times \cos(30°)}$$
$$= \sqrt{0{,}0144 + 0{,}0100 - 0{,}0240 \times 0{,}8660}$$
$$= \sqrt{0{,}0244 - 0{,}02078}$$
$$= \sqrt{0{,}00362} = 0{,}0602 \, \text{m}$$

*Attention* : cette longueur représente la distance entre les deux points d'accroche (triangle), pas la longueur totale du ressort. En ajoutant la longueur au repos du ressort (non demandée dans ce calcul de vérification), on retrouverait $L_\text{max} \approx 280 \, \text{mm}$.

**Pour $\theta_1 = 150°$** :
$$L(150°) = \sqrt{0{,}12^2 + 0{,}10^2 - 2 \times 0{,}12 \times 0{,}10 \times \cos(150° + 30°)}$$
$$= \sqrt{0{,}0244 - 0{,}0240 \times \cos(180°)}$$
$$= \sqrt{0{,}0244 - 0{,}0240 \times (-1)}$$
$$= \sqrt{0{,}0244 + 0{,}0240} = \sqrt{0{,}0484} = 0{,}220 \, \text{m}$$

**Course effective** :
$$c_\text{eff} = L(150°) - L(0°) = 0{,}220 - 0{,}0602 = 0{,}160 \, \text{m} = 160 \, \text{mm}$$

> Mais le cahier des charges indique une course de 120 mm. On note que notre calcul donne 160 mm, ce qui signifie que le ressort doit avoir une course d'au moins 160 mm pour couvrir l'amplitude 0°–150°. **Il y a une non-conformité** : soit il faut allonger la course du ressort à 160 mm, soit réduire les bras de levier $d_0$ et $d_2$.

**Conclusion** : Le critère de course n'est pas respecté en l'état ($c_\text{eff} = 160 \, \text{mm} > 120 \, \text{mm}$). Une modification géométrique (réduction de $d_0$ à 0,09 m par exemple) serait nécessaire pour ramener la course à 120 mm tout en maintenant l'amplitude de 150°.

---

## PARTIE C — Dimensionnement statique

---

### Corrigé C8 — Isolement et bilan des actions

#### Q C8.a — Bilan des actions à $\theta_1 = 90°$

Le système isolé est $\Sigma = \{S2 + \text{bras opérateur} + \text{outil}\}$.

**Actions extérieures s'appliquant sur $\Sigma$** :

1. **Poids de S2** : $\vec{P}_{S2} = -m_2 \cdot g \cdot \vec{z} = -0{,}45 \times 9{,}81 \cdot \vec{z} = -4{,}41 \, \vec{z} \, \text{N}$, appliqué en $G_2$ à $0{,}16 \, \text{m}$ de $\Delta_1$ (sur l'horizontale)

2. **Poids du bras opérateur** : $\vec{P}_\text{bras} = -m_\text{bras} \cdot g \cdot \vec{z} = -4{,}0 \times 9{,}81 \cdot \vec{z} = -39{,}24 \, \vec{z} \, \text{N}$, appliqué à $0{,}30 \, \text{m}$ de $\Delta_1$

3. **Poids de l'outil** : $\vec{P}_\text{outil} = -m_\text{outil} \cdot g \cdot \vec{z} = -2{,}0 \times 9{,}81 \cdot \vec{z} = -19{,}62 \, \vec{z} \, \text{N}$, appliqué à $0{,}60 \, \text{m}$ de $\Delta_1$

4. **Force du ressort R1** : $\vec{F}_{R1}$ de norme $F_{R1}$ (inconnue), dirigée selon l'axe du ressort (angle $\alpha = 40°$ avec l'horizontale), appliquée en B

5. **Réaction en $\Delta_1$** (liaison pivot S0/S1) : $\vec{R}_{\Delta_1} = R_x \cdot \vec{x} + R_z \cdot \vec{z}$ (inconnues)

```
Schéma PFS — Vue de côté (plan sagittal), bras horizontal (θ₁ = 90°) :

    S0 (bâti)
    │
    ●─── Δ₁ (pivot) ──────────────────────────────→ x
    │        R_x→                              ●─── extrémité bras
    │R_z↑                           G_bras ●       + outil
    │
    ╔══════════════════════════════════════════╗
    ║  S2 + bras opérateur + outil             ║
    ╚══════════════════════════════════════════╝
              │           │             │
             P_S2↓      P_bras↓      P_outil↓
         (0.16 m)    (0.30 m)      (0.60 m)
    
    F_R1 appliquée en B (d₂ = 0.10 m de Δ₁)
    à 40° avec l'horizontale (composante verticale vers le haut)
```

#### Q C8.b — Équations d'équilibre

**Équation de translation selon $\vec{x}$** :
$$\sum F_x = 0 : R_x - F_{R1} \cos(40°) = 0$$

**Équation de translation selon $\vec{z}$** :
$$\sum F_z = 0 : R_z + F_{R1} \sin(40°) - P_{S2} - P_\text{bras} - P_\text{outil} = 0$$

**Équation de moment par rapport à $\Delta_1$** (sens positif trigonométrique) :
$$\sum M_{\Delta_1} = 0 :$$
$$F_{R1} \sin(40°) \cdot d_2 - P_{S2} \cdot \frac{L_2}{2} - P_\text{bras} \cdot l_G - P_\text{outil} \cdot l_\text{outil} = 0$$

*Remarque* : Les forces de poids (vers le bas) créent un couple résistant (sens horaire → négatif) ; la composante verticale du ressort crée un couple moteur (vers le haut → positif). Les composantes horizontales des forces de poids sont nulles (les poids sont verticaux et appliqués sur un bras horizontal → bras de levier = coordonnée horizontale).

---

### Corrigé C9 — Calcul de l'effort du ressort

#### Q C9.a — Expression de $F_{R1}$

De l'équation de moment en $\Delta_1$ :

$$F_{R1} \cdot \sin(40°) \cdot d_2 = P_{S2} \cdot \frac{L_2}{2} + P_\text{bras} \cdot l_G + P_\text{outil} \cdot l_\text{outil}$$

$$\boxed{F_{R1} = \frac{m_2 \cdot g \cdot \frac{L_2}{2} + m_\text{bras} \cdot g \cdot l_G + m_\text{outil} \cdot g \cdot l_\text{outil}}{\sin(40°) \cdot d_2}}$$

#### Q C9.b — Application numérique

Numérateur :
$$N = 0{,}45 \times 9{,}81 \times 0{,}16 + 4{,}0 \times 9{,}81 \times 0{,}30 + 2{,}0 \times 9{,}81 \times 0{,}60$$
$$= 0{,}706 + 11{,}772 + 11{,}772 = 24{,}25 \, \text{N·m}$$

Dénominateur :
$$D = \sin(40°) \times 0{,}10 = 0{,}6428 \times 0{,}10 = 0{,}06428 \, \text{m}$$

$$\boxed{F_{R1} = \frac{24{,}25}{0{,}06428} \approx 377 \, \text{N}}$$

**Comparaison** : La force nominale du ressort est $F_0 = 180 \, \text{N}$, ce qui est nettement inférieur à la valeur nécessaire pour une compensation à 100 %. Cela est cohérent car l'exosquelette ne compense que **40 % de l'effort** — on peut vérifier ci-dessous.

#### Q C9.c — Vérification de la compensation à 40 %

Couple musculaire sans exosquelette :
$$M_\text{musc,sans} = (m_\text{bras} \cdot l_G + m_\text{outil} \cdot l_\text{outil}) \cdot g \cdot \sin(90°)$$
$$= (4{,}0 \times 0{,}30 + 2{,}0 \times 0{,}60) \times 9{,}81 \times 1$$
$$= (1{,}20 + 1{,}20) \times 9{,}81 = 2{,}40 \times 9{,}81 = 23{,}54 \, \text{N·m}$$

Couple d'assistance du ressort :
$$M_\text{assist} = F_{R1} \cdot \sin(40°) \cdot d_2 = 377 \times 0{,}6428 \times 0{,}10 \approx 24{,}2 \, \text{N·m}$$

> *Note* : Cette valeur correspond à une compensation de $M_\text{S2}$ inclus. Si on recalcule pour 40 % de $M_\text{musc,sans}$ :
> $$40\% \times M_\text{musc,sans} = 0{,}40 \times 23{,}54 = 9{,}42 \, \text{N·m}$$
> Ce qui donnerait $F_{R1} = 9{,}42 / (0{,}6428 \times 0{,}10) \approx 147 \, \text{N}$, cohérent avec $F_0 = 180 \, \text{N}$ (à 40° d'angle, la composante efficace est $\sin(\alpha')$).

**Conclusion** : Avec $F_0 = 180 \, \text{N}$ et le bras de levier de $d_2 = 0{,}10 \, \text{m}$, le couple d'assistance est de l'ordre de 11,5 à 12 N·m, soit **environ 48 % de $M_\text{musc,sans}$**, ce qui est conforme à l'objectif de 40 % ± 5 % du cahier des charges.

---

### Corrigé C10 — Contrainte dans l'axe d'articulation

#### Q C10.a — Section transversale de l'axe creux

$$S_\text{axe} = \frac{\pi}{4}(d_e^2 - d_i^2) = \frac{\pi}{4}(0{,}016^2 - 0{,}010^2)$$
$$= \frac{\pi}{4}(256 \times 10^{-6} - 100 \times 10^{-6})$$
$$= \frac{\pi}{4} \times 156 \times 10^{-6}$$

$$\boxed{S_\text{axe} = 122{,}5 \, \text{mm}^2 = 1{,}225 \times 10^{-4} \, \text{m}^2}$$

#### Q C10.b — Réaction en $\Delta_1$

De l'équation de translation selon $\vec{x}$ (avec $F_{R1} = 180 \, \text{N}$ pour une compensation à 40 %) :
$$R_x = F_{R1} \cdot \cos(40°) = 180 \times 0{,}766 = 137{,}9 \, \text{N}$$

De l'équation de translation selon $\vec{z}$ :
$$R_z = P_{S2} + P_\text{bras} + P_\text{outil} - F_{R1} \cdot \sin(40°)$$
$$= 4{,}41 + 39{,}24 + 19{,}62 - 180 \times 0{,}6428$$
$$= 63{,}27 - 115{,}7 = -52{,}4 \, \text{N}$$

Norme de la réaction :
$$R_{\Delta_1} = \sqrt{R_x^2 + R_z^2} = \sqrt{137{,}9^2 + (-52{,}4)^2}$$
$$= \sqrt{19{,}016 + 2{,}746} \times 10^3 = \sqrt{21{,}762 \times 10^3}$$

$$\boxed{R_{\Delta_1} = \sqrt{R_x^2 + R_z^2} \approx 147{,}6 \, \text{N}}$$

#### Q C10.c — Vérification critère de Von Mises

Contrainte de cisaillement :
$$\tau = \frac{R_{\Delta_1}}{S_\text{axe}} = \frac{147{,}6}{1{,}225 \times 10^{-4}} = 1{,}205 \times 10^6 \, \text{Pa}$$

$$\boxed{\tau \approx 1{,}2 \, \text{MPa}}$$

Contrainte équivalente de Von Mises :
$$\sigma_\text{eq} = \sqrt{3} \cdot \tau = 1{,}732 \times 1{,}2 = 2{,}08 \, \text{MPa}$$

Limite admissible :
$$\sigma_\text{adm} = \frac{R_e}{s} = \frac{650}{2} = 325 \, \text{MPa}$$

**Vérification** : $\sigma_\text{eq} = 2{,}08 \, \text{MPa} \ll \sigma_\text{adm} = 325 \, \text{MPa}$ ✔

**Conclusion** : L'axe est **largement dimensionné**. Le coefficient de sécurité réel est $s_\text{réel} = 650 / (2{,}08/\sqrt{3}) \approx 540$, ce qui laisse une très grande marge. Une réduction du diamètre serait possible pour alléger l'axe, mais au vu des contraintes de fabrication et de fiabilité, $d_e = 16 \, \text{mm}$ est une valeur raisonnable en milieu industriel.

---

## PARTIE D — Résistance des matériaux

---

### Corrigé D11 — Modélisation de la poutre

#### Q D11.a — Schématisation

```
z
↑
│    A (encastrement)                    B (extrémité libre)
│    ║══════════════════════════════════════●
│    ║◄──────────── L = 0,40 m ───────────►│
│                                          ↓
│                                       F = 85 N (vers le bas)
│
│    Conditions aux limites :
│    - En A : déplacement nul, rotation nulle (encastrement)
│    - En B : moment nul, effort tranchant = F (charge concentrée)
│
│    Sollicitation : FLEXION PURE (moment fléchissant + effort tranchant)
```

La poutre est soumise à une **flexion plane** dans le plan $(x, z)$ par la force concentrée $F$ en B.

#### Q D11.b — Moment d'inertie $I_z$

Section rectangulaire creuse : $b = 30 \, \text{mm}$, $h = 20 \, \text{mm}$, $e = 2 \, \text{mm}$

$$I_z = \frac{b \cdot h^3 - (b-2e)(h-2e)^3}{12}$$

$$= \frac{30 \times 20^3 - (30 - 4)(20 - 4)^3}{12}$$

$$= \frac{30 \times 8000 - 26 \times 4096}{12}$$

$$= \frac{240\,000 - 106\,496}{12}$$

$$= \frac{133\,504}{12}$$

$$\boxed{I_z = 11\,125 \, \text{mm}^4 = 1{,}113 \times 10^{-8} \, \text{m}^4}$$

---

### Corrigé D12 — Diagrammes des efforts intérieurs

#### Q D12.a — Expressions de $T(x)$ et $M_f(x)$

On oriente $x$ de A (encastrement, $x=0$) vers B (extrémité libre, $x=L$).

**Méthode des coupes** : on coupe en $x$ et on isole la partie droite (de $x$ à $B$).

Sur la partie droite, la seule force extérieure est $\vec{F} = -F \vec{z}$ en $B$, soit :

- **Effort tranchant** :
$$T(x) = F = 85 \, \text{N} \quad \forall x \in [0, L]$$

*Remarque sur le signe* : selon la convention des efforts intérieurs (cohérent avec traction-compression et flexion), $T$ est constant et vaut $+F$ (ou $-F$ selon la convention adoptée — on retiendra $|T| = 85 \, \text{N}$).

- **Moment fléchissant** (par rapport à la section courante, en isolant la partie de $x$ à $B$) :
$$M_f(x) = -F \cdot (L - x) \quad \forall x \in [0, L]$$

*Valeurs caractéristiques* :
- En $x = 0$ (encastrement) : $M_f(0) = -F \cdot L = -85 \times 0{,}40 = -34 \, \text{N·m}$
- En $x = L$ (extrémité libre) : $M_f(L) = 0$

#### Q D12.b — Diagrammes

```
T(x) [N]
 85 │████████████████████████████████████
    │
  0 └──────────────────────────────────── x
    A (x=0)                           B (x=L)
    
    T(x) = constante = 85 N (la force de cisaillement est uniforme)
```

```
M_f(x) [N·m]
  0  ┐──────────────────────────────────── x
     │                                  /
 -17 │                          /
     │                  /
 -34 │          /
     └──────────────────────────────────── 
     A (x=0)                           B (x=L)
     M_f(0) = -34 N·m                  M_f(L) = 0

    M_f(x) est une droite de pente +F = +85 N,
    croissant de -34 N·m (en A) à 0 (en B)
```

**Le moment maximal en valeur absolue est en A (encastrement) : $|M_{f,\text{max}}| = 34 \, \text{N·m}$**

---

### Corrigé D13 — Flèche maximale et critère de rigidité

#### Q D13.a — Flèche maximale

$$f_\text{max} = \frac{F \cdot L^3}{3 \cdot E \cdot I_z}$$

Application numérique :
- $F = 85 \, \text{N}$
- $L = 0{,}40 \, \text{m}$
- $E = 71 \times 10^9 \, \text{Pa}$
- $I_z = 1{,}113 \times 10^{-8} \, \text{m}^4$

$$f_\text{max} = \frac{85 \times (0{,}40)^3}{3 \times 71 \times 10^9 \times 1{,}113 \times 10^{-8}}$$

$$= \frac{85 \times 0{,}064}{3 \times 790{,}2}$$

$$= \frac{5{,}44}{2370{,}6}$$

$$\boxed{f_\text{max} = 2{,}30 \times 10^{-3} \, \text{m} = 2{,}30 \, \text{mm}}$$

#### Q D13.b — Vérification du critère de rigidité

Critère : $f_\text{max} \leq L/200$

$$\frac{L}{200} = \frac{0{,}40}{200} = 0{,}002 \, \text{m} = 2 \, \text{mm}$$

**Vérification** : $f_\text{max} = 2{,}30 \, \text{mm} > L/200 = 2{,}00 \, \text{mm}$ ✗

**Le critère n'est pas respecté** (la flèche calculée est légèrement supérieure à la limite). L'écart est de $+15 \%$.

#### Q D13.c — Modification de section

Pour satisfaire le critère, il faut augmenter $I_z$ d'au moins 15 %. En maintenant la même masse de matière (même section), on peut **redistribuer la matière** :
- Augmenter la hauteur $h$ de 20 mm à 22 mm (en réduisant proportionnellement l'épaisseur)
- Passer à un profilé en **I** ou en **U** qui offre un meilleur rapport $I_z / S$ (section)

*Alternative* : augmenter $h$ de 2 mm (de 20 à 22 mm) tout en gardant $b = 30 \, \text{mm}$ et $e = 2 \, \text{mm}$ :

$$I_{z,\text{new}} = \frac{30 \times 22^3 - 26 \times 18^3}{12} = \frac{319\,440 - 151\,632}{12} = \frac{167\,808}{12} = 13\,984 \, \text{mm}^4$$

Nouvelle flèche :
$$f'_\text{max} = f_\text{max} \times \frac{I_z}{I_{z,\text{new}}} = 2{,}30 \times \frac{11\,125}{13\,984} = 2{,}30 \times 0{,}796 = 1{,}83 \, \text{mm} < 2 \, \text{mm}$$ ✔

---

### Corrigé D14 — Comparaison de matériaux

#### Q D14.a — Rapport des moments d'inertie

Pour une rigidité identique : $E_C \cdot I_{z,C} = E_{Al} \cdot I_{z,Al}$

$$\frac{I_{z,C}}{I_{z,Al}} = \frac{E_{Al}}{E_C} = \frac{71}{135} = 0{,}526$$

La section composite doit donc avoir un moment d'inertie **plus faible** que l'aluminium (car son module est plus élevé), ce qui est favorable.

Pour une section rectangulaire creuse avec $b$ constant : $I_z \propto h^3$ (approximation pour parois minces)

$$\frac{h_C}{h_{Al}} = \left(\frac{I_{z,C}}{I_{z,Al}}\right)^{1/3} = (0{,}526)^{1/3} = 0{,}807$$

Soit $h_C = 0{,}807 \times 20 = 16{,}1 \, \text{mm}$ ≈ 16 mm.

$$\boxed{\frac{I_{z,C}}{I_{z,Al}} = 0{,}526 \quad ; \quad \frac{h_C}{h_{Al}} \approx 0{,}81}$$

#### Q D14.b — Gain de masse

En supposant $b$ et $e$ constants, et $h_C = 16 \, \text{mm}$ vs $h_{Al} = 20 \, \text{mm}$ :

Section composite : $S_C = b \cdot h_C - (b-2e)(h_C-2e)^3 / h_C$ (approximation section mince) :
$$S_C \approx 2 \times e \times (b + h_C - 2e) = 2 \times 2 \times (30 + 16 - 4) = 4 \times 42 = 168 \, \text{mm}^2$$

Section aluminium :
$$S_{Al} \approx 2 \times 2 \times (30 + 20 - 4) = 4 \times 46 = 184 \, \text{mm}^2$$

Rapport des masses (longueur identique) :
$$\frac{m_C}{m_{Al}} = \frac{S_C \cdot \rho_C}{S_{Al} \cdot \rho_{Al}} = \frac{168 \times 1\,550}{184 \times 2\,810} = \frac{260\,400}{516\,640} = 0{,}504$$

$$\boxed{\text{Gain de masse} = 1 - 0{,}504 = 49{,}6\% \approx 50\%}$$

**Conclusion** : Le passage au composite carbone/époxy permet de **réduire la masse de la barre de support de près de 50 %** tout en maintenant la même rigidité. C'est un argument fort en faveur du composite, au prix d'un coût de fabrication plus élevé.

---

## PARTIE E — Modélisation dynamique

---

### Corrigé E15 — Modèle dynamique

#### Q E15.a — Équation du PFD en rotation

Le PFD appliqué au solide équivalent (bras + outil + S2) en rotation autour de $\Delta_1$ :

$$J \cdot \ddot{\theta}_1 = C_\text{ressort} + C_\text{musc} - C_\text{grav}(\theta_1) - C_\text{frot}$$

Avec :
- $J = 0{,}75 \, \text{kg·m}^2$ (moment d'inertie total)
- $C_\text{ressort}(\theta_1) = F_{R1}(\theta_1) \cdot d_2 \cdot \sin(\alpha(\theta_1))$ (couple d'assistance du ressort, moteur)
- $C_\text{musc}$ : couple des muscles de l'épaule (moteur)
- $C_\text{grav}(\theta_1) = (m_\text{bras} \cdot l_G + m_\text{outil} \cdot l_\text{outil}) \cdot g \cdot \cos(\theta_1)$ (couple résistant gravitaire)
- $C_\text{frot}$ : couple de frottement dans les articulations (résistant, supposé nul ici)

Le sens positif est le sens de levée du bras (angle $\theta_1$ croissant).

#### Q E15.b — Simplification (couple musculaire nul)

Avec $C_\text{musc} = 0$ et $C_\text{ressort} = 25 \, \text{N·m}$ (constant) :

$$\boxed{J \cdot \ddot{\theta}_1 = 25 - (m_\text{bras} \cdot l_G + m_\text{outil} \cdot l_\text{outil}) \cdot g \cdot \cos(\theta_1)}$$

$$0{,}75 \cdot \ddot{\theta}_1 = 25 - (4{,}0 \times 0{,}30 + 2{,}0 \times 0{,}60) \times 9{,}81 \times \cos(\theta_1)$$

$$0{,}75 \cdot \ddot{\theta}_1 = 25 - 23{,}54 \cdot \cos(\theta_1)$$

---

### Corrigé E16 — Couple résistant en fonction de la vitesse

#### Q E16.a — Calcul à $\theta_1 = 45°$, $\dot{\theta}_1 = 1{,}5 \, \text{rad/s}$

**Couple gravitaire** :
$$C_\text{grav}(45°) = 23{,}54 \times \cos(45°) = 23{,}54 \times 0{,}7071 = 16{,}65 \, \text{N·m}$$

**Terme d'amortissement** :
$$b \cdot \dot{\theta}_1 = 0{,}8 \times 1{,}5 = 1{,}20 \, \text{N·m}$$

**Équation dynamique** :
$$J \cdot \ddot{\theta}_1 = C_\text{ressort} - C_\text{grav} - b \cdot \dot{\theta}_1 = 25 - 16{,}65 - 1{,}20 = 7{,}15 \, \text{N·m}$$

$$\ddot{\theta}_1 = \frac{7{,}15}{J} = \frac{7{,}15}{0{,}75}$$

$$\boxed{\ddot{\theta}_1 \approx 9{,}53 \, \text{rad/s}^2}$$

#### Q E16.b — Vitesse limite à $\theta_1 = 45°$

$\ddot{\theta}_1 = 0$ quand :
$$C_\text{ressort} - C_\text{grav}(45°) - b \cdot \dot{\theta}_{1,\text{lim}} = 0$$

$$\dot{\theta}_{1,\text{lim}} = \frac{C_\text{ressort} - C_\text{grav}(45°)}{b} = \frac{25 - 16{,}65}{0{,}8} = \frac{8{,}35}{0{,}8}$$

$$\boxed{\dot{\theta}_{1,\text{lim}} \approx 10{,}4 \, \text{rad/s} \approx 596°/s}$$

**Interprétation** : À 45° d'angle d'épaule, si la vitesse angulaire atteint 10,4 rad/s, le couple d'amortissement compense exactement la différence entre le couple du ressort et le couple gravitaire. Au-delà de cette vitesse, la deceleration serait. En pratique, cette vitesse est très élevée pour un mouvement de bras humain (typiquement < 3 rad/s) → l'amortissement n'est jamais saturant dans les conditions normales d'utilisation.

---

### Corrigé E17 — Temps de réponse

#### Q E17.a — Accélération angulaire constante

Pour un mouvement de 0° à 90° ($\theta_\text{final} = \pi/2 \, \text{rad}$) en $t_f = 0{,}8 \, \text{s}$, avec départ à repos et arrivée à l'arrêt (profil trapézoïdal symétrique) :

$$\theta_\text{final} = \frac{1}{2} \cdot \ddot{\theta}_1 \cdot t_f^2 \quad \text{(profil tout-ou-rien, pour simplifier)}$$

$$\ddot{\theta}_1 = \frac{2 \cdot \theta_\text{final}}{t_f^2} = \frac{2 \times \frac{\pi}{2}}{(0{,}8)^2} = \frac{\pi}{0{,}64}$$

$$\boxed{\ddot{\theta}_1 \approx 4{,}91 \, \text{rad/s}^2}$$

#### Q E17.b — Couple total

$$C_\text{total} = J \cdot \ddot{\theta}_1 = 0{,}75 \times 4{,}91$$

$$\boxed{C_\text{total} \approx 3{,}68 \, \text{N·m}}$$

#### Q E17.c — Vérification de l'amortissement à mi-course

À $t = 0{,}4 \, \text{s}$ :
$$\dot{\theta}_1 = \ddot{\theta}_1 \times t = 4{,}91 \times 0{,}4 = 1{,}96 \, \text{rad/s}$$

Terme d'amortissement :
$$b \cdot \dot{\theta}_1 = 0{,}8 \times 1{,}96 = 1{,}57 \, \text{N·m}$$

Rapport au couple total :
$$\frac{b \cdot \dot{\theta}_1}{C_\text{total}} = \frac{1{,}57}{3{,}68} = 42{,}7\%$$

**Le terme d'amortissement représente environ 43 % du couple total**, ce qui n'est pas négligeable. La simplification "amortissement < 10 %" n'est pas vérifiée pour ce mouvement rapide. Pour modéliser plus précisément, il faudrait prendre en compte l'amortissement dans l'équation du mouvement (résolution numérique).

#### Q E17.d — Puissance mécanique moyenne

Vitesse angulaire moyenne :
$$\dot{\theta}_{1,\text{moy}} = \frac{\theta_\text{final}}{t_f} = \frac{\pi/2}{0{,}8} = \frac{1{,}571}{0{,}8} = 1{,}96 \, \text{rad/s}$$

Puissance moyenne :
$$P_\text{moy} = C_\text{total} \times \dot{\theta}_{1,\text{moy}} = 3{,}68 \times 1{,}96$$

$$\boxed{P_\text{moy} \approx 7{,}2 \, \text{W}}$$

#### Q E17.e — Commentaire ergonomique

La puissance développée par le système (muscles + exosquelette) pour lever le bras en 0,8 s est d'environ **7,2 W**, ce qui est **très en dessous** de la limite de 50 W pour un travail répétitif à l'épaule. Cela illustre l'intérêt de l'exosquelette : en fournissant 25 N·m de couple d'assistance, il réduit considérablement la puissance musculaire requise pour des tâches de levée répétitives, repoussant le seuil de fatigue.

---

## PARTIE F — Synthèse

---

### Corrigé F18 — Tableau de synthèse des performances

| Exigence | Valeur visée | Valeur modélisée | Écart | Conforme ? |
|---|---|---|---|---|
| Réduction effort musculaire | 40 % | ~48 % (avec $F_0 = 180 \, \text{N}$, $d_2 = 0{,}10 \, \text{m}$) | +8 % | ✔ (dans fourchette 30–50 %) |
| Amplitude flexion d'épaule | 0° à 150° | Limitée par course ressort (160 mm req., 120 mm disponibles) | Non satisfait en l'état | ✗ (modification nécessaire) |
| Flèche barre support ($f \leq L/200$) | $\leq 2 \, \text{mm}$ | $2{,}30 \, \text{mm}$ | +15 % | ✗ (légèrement dépassé) |
| Contrainte dans l'axe | $\leq 325 \, \text{MPa}$ | $\approx 2 \, \text{MPa}$ | Très inférieur | ✔ (très large marge) |
| Levée bras 0°→90° en $\leq 0{,}8$ s | $\leq 0{,}8 \, \text{s}$ | Compatible avec puissance disponible | ~0 % | ✔ |

**Conclusion générale** : Le concept EXOARM-S3 est **globalement validé** dans ses grandes lignes. Deux points nécessitent un travail de conception supplémentaire : (1) la course du ressort à gaz (allonger de 120 à 160 mm, ou revoir la géométrie des bras de levier), et (2) la rigidité de la barre de support (augmenter légèrement la hauteur de section ou changer de matériau). Les aspects résistance et sécurité sont largement satisfaits.

---

### Corrigé F19 — Améliorations de conception

#### Q F19.a — Limites du modèle statique

1. **Le corps humain est modélisé comme un bras rigide** : en réalité, le bras de l'opérateur est articulé (épaule + coude + poignet), et la masse et le centre de gravité varient selon la posture réelle.

2. **La force du ressort est supposée constante ($F_0 = 180 \, \text{N}$)** : or le cahier des charges indique une variation de ±15 N sur la course. La force d'assistance dépend donc de l'angle $\theta_1$, ce qui modifie le niveau de compensation selon la position bras.

#### Q F19.b — Améliorations techniques

1. **Ajout d'un module de réglage de raideur du ressort** (réglage par vis de précontrainte) : permettrait d'adapter la force d'assistance selon la charge de l'outil (de 0 à 5 kg), améliorant la polyvalence.

2. **Remplacement de la barre de support aluminium par du carbone/époxy** (cf. Partie D) : gain de masse de 50 % sur ce composant, améliorant le confort de port et réduisant la fatigue globale due à la masse de l'exosquelette lui-même.

---

### Corrigé F20 — Impact sociétal et environnemental

#### Q F20.a — Parties prenantes

| Partie prenante | Intérêt |
|---|---|
| **Opérateur** | Réduction de la douleur et de la fatigue, protection de la santé, confort au travail |
| **Entreprise** | Réduction du nombre de TMS (coût humain, absences, AT/MP), productivité maintenue voire améliorée, image RSE |
| **Société** | Réduction des coûts de santé publique (soins, invalidité), maintien de l'emploi de travailleurs seniors |
| **Environnement** | Fabrication (matériaux, énergie), fin de vie (recyclabilité de l'aluminium ++, composite –) |

#### Q F20.b — ACV de l'EXOARM-S3

L'**Analyse du Cycle de Vie** (ACV, norme ISO 14040/14044) identifie les impacts environnementaux à chaque étape :

| Phase | Principaux impacts |
|---|---|
| **Extraction/fabrication** | Énergie de production de l'aluminium (très énergivore : ~200 MJ/kg), composite difficile à produire, usinage des pièces |
| **Utilisation** | Impact faible (système passif, pas de consommation énergétique, pas d'émissions directes) ; mais transport quotidien de l'opérateur portant +3,5 kg |
| **Maintenance** | Remplacement des ressorts à gaz (2M cycles ≈ 5 ans d'utilisation intense) → déchets limités |
| **Fin de vie** | Aluminium recyclable à 95 % avec économie d'énergie de 95 % ; composite carbone peu recyclable (valorisation thermique principalement) |

*Bilan* : Le principal hotspot environnemental est la **fabrication** (en particulier l'aluminium). La durée de vie longue (> 10 ans) et la recyclabilité de l'aluminium sont des points positifs. Le recours aux composites améliore les performances mais dégrade le bilan fin de vie.

#### Q F20.c — Exosquelette : substitution ou amélioration du travail ?

L'introduction d'exosquelettes passifs comme l'EXOARM-S3 ne **substitue pas** le travail humain mais en **améliore les conditions**. L'opérateur continue d'effectuer les mêmes gestes — vissage, câblage, peinture — mais avec un effort musculaire réduit de 30 à 50 % à l'épaule. La décision est toujours humaine, la dextérité est inchangée. En revanche, l'exosquelette permet à des travailleurs vieillissants ou en reprise après blessure de rester en activité plus longtemps, ce qui est un levier de maintien dans l'emploi. Les risques à surveiller sont l'effet de "report" de la charge vers d'autres articulations (hanche, dos), si l'exosquelette n'est pas bien réglé, et le risque de dépendance à l'outil pour des gestes qui pourraient autrement être organisés différemment (rotation des postes, reconception des postes de travail).

---

*— Fin du corrigé —*
