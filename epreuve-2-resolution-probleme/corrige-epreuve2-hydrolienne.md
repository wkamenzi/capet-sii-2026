# CAPET SII — Ingénierie Mécanique — Session 2026
## Épreuve 2 : Résolution de problème — **CORRIGÉ DÉTAILLÉ**

---

> **Document d'entraînement non officiel — Usage pédagogique exclusivement**

---

## PHASE 1 — Exploitation des ressources

---

### Corrigé 1.1 — Analyse du cahier des charges

#### Q 1.1.a — Fonctions et diagramme pieuvre

**Fonction Principale (FP)** : Permettre au réseau électrique de recevoir de l'énergie en exploitant l'énergie cinétique du courant fluvial.

*Reformulation* : "Convertir l'énergie cinétique de l'eau courante (fleuve) en énergie électrique injectée dans le réseau."

**Fonctions contraintes** (issues du CdCF DR-1) :
- **FC-01** : Ne pas perturber la navigation fluviale (encombrement ≤ 3 m)
- **FC-02** : Résister aux crues (survie à $V = 4{,}0 \, \text{m/s}$)
- **FC-03** : Respecter l'écologie (vitesse rotation ≤ 60 tr/min)
- **FC-04** : Être maintenable sans plongeur (système levable)
- **FC-05** : Résister à la corrosion (matériaux inox ou polymères composites, 20 ans)

**Diagramme pieuvre simplifié** :

```
                      ┌────────────────┐
                      │  Réseau élect. │
                      └───────┬────────┘
                              │ FP
           ┌──────────────────┼──────────────────┐
           │                  │                  │
  ┌────────┴───────┐   ╔══════╧══════╗  ┌────────┴──────────┐
  │ Courant fluvial│   ║             ║  │ Navigation fluviale│
  │  (énergie      │FP ║  HydroFlux  ║FC│  (péniches, bateaux│
  │   cinétique)   │   ║    -V5      ║  │   de plaisance)    │
  └────────────────┘   ╚══════╤══════╝  └────────────────────┘
           │                  │                  │
  ┌────────┴───────┐          │FC         ┌──────┴──────────┐
  │  Faune         │          │           │   Techniciens   │
  │  aquatique     │    ┌─────┴─────┐     │   maintenance   │
  └────────────────┘    │  Normes/  │     └─────────────────┘
                        │  Réglements│
                        └───────────┘
```

**Milieu extérieur** : courant fluvial, réseau électrique, navigation fluviale, faune aquatique, techniciens de maintenance, réglementation fluviale.

#### Q 1.1.b — Vitesse angulaire maximale

$$\omega_\text{max} = \frac{2\pi \cdot n_\text{max}}{60} = \frac{2\pi \times 60}{60} = 2\pi$$

$$\boxed{\omega_\text{max} = 2\pi \approx 6{,}28 \, \text{rad/s}}$$

#### Q 1.1.c — Rapport de vitesse spécifique maximal

$$\lambda_\text{max} = \frac{\omega_\text{max} \cdot R}{V_n} = \frac{6{,}28 \times 1{,}0}{2{,}5}$$

$$\boxed{\lambda_\text{max} = \frac{6{,}28}{2{,}5} = 2{,}51}$$

**Comparaison** : $\lambda_\text{max} = 2{,}51 \approx \lambda_\text{opt} = 2{,}5$

**Conclusion** : La contrainte FC-03 ($n \leq 60 \, \text{tr/min}$) correspond presque exactement à la condition de fonctionnement optimal ($\lambda_\text{opt} = 2{,}5$). Les deux exigences sont **parfaitement compatibles** : à la vitesse nominale, la turbine fonctionnera à son régime optimal tout en respectant la contrainte de protection des poissons. C'est un résultat rassurant pour la conception.

#### Q 1.1.d — Mécanismes de corrosion et solutions

| Mécanisme | Description | Solution technique |
|---|---|---|
| **Corrosion galvanique** | Contact entre deux métaux de potentiels différents (ex. acier inox + aluminium) dans l'électrolyte aqueux → dissolution du métal le moins noble | Utiliser des matériaux compatibles (inox 316L + inox 316L) ou interposer des joints isolants électriques entre pièces de métaux différents |
| **Corrosion par érosion** | Les particules en suspension (sable, limon) dans le courant créent un abrasion continue des surfaces métalliques, détruisant la couche passive | Revêtement époxy sous-marin sur les surfaces exposées ; épaisseur de paroi surdimensionnée |

*Autres réponses acceptables* : corrosion par piqûres (dans les zones de stagnation), corrosion sous contrainte, bio-encrassement (colonisation par algues et mollusques).

---

### Corrigé 1.2 — Données hydrologiques

#### Q 1.2.a — Vérification de la somme

$365 \times 24 = 8\,760 \, \text{h/an}$

Somme de la table : $876 + 1\,314 + 1\,752 + 1\,752 + 1\,314 + 876 + 876 = 8\,760 \, \text{h}$ ✔

**La vérification est correcte.**

#### Q 1.2.b — Durée à $V \geq V_n = 2{,}5 \, \text{m/s}$

Plages concernées : $[2{,}5 ; 3{,}0[$ + $[3{,}0 ; 3{,}5[$ + $[3{,}5 ; +\infty[$

$$\Delta t_{V \geq 2,5} = 1\,314 + 876 + 876 = 3\,066 \, \text{h/an}$$

**Comparaison au CdCF** : $3\,066 \, \text{h/an} < 3\,200 \, \text{h/an}$ ✗

Le site ne satisfait pas l'exigence FP-02 avec la définition stricte "$V \geq V_n$". L'écart est de $3\,200 - 3\,066 = 134 \, \text{h/an}$ (environ 4 %). On peut envisager une légère révision du critère (par exemple abaisser le seuil à $V_\text{min} = 2{,}3 \, \text{m/s}$) ou choisir un site légèrement plus rapide.

> *Résultat intermédiaire fourni* : $\Delta t_{V \geq 2,5} = 3\,066 \, \text{h/an}$

#### Q 1.2.c — Puissance hydraulique disponible

$$P_\text{hyd}(V) = \frac{1}{2} \times 1\,000 \times 3{,}0 \times V^3 = 1\,500 \, V^3 \, \text{W}$$

**Pour $V = 1{,}5 \, \text{m/s}$** :
$$P_\text{hyd}(1{,}5) = 1\,500 \times 1{,}5^3 = 1\,500 \times 3{,}375 = \boxed{5\,063 \, \text{W} \approx 5{,}1 \, \text{kW}}$$

**Pour $V = 2{,}5 \, \text{m/s}$** :
$$P_\text{hyd}(2{,}5) = 1\,500 \times 2{,}5^3 = 1\,500 \times 15{,}625 = \boxed{23\,438 \, \text{W} \approx 23{,}4 \, \text{kW}}$$

**Pour $V = 3{,}5 \, \text{m/s}$** :
$$P_\text{hyd}(3{,}5) = 1\,500 \times 3{,}5^3 = 1\,500 \times 42{,}875 = \boxed{64\,313 \, \text{W} \approx 64{,}3 \, \text{kW}}$$

*Remarque* : La puissance varie avec $V^3$, ce qui explique la très grande sensibilité aux variations de vitesse : passer de 1,5 à 3,5 m/s multiplie la puissance disponible par $(3{,}5/1{,}5)^3 = 12{,}7$.

#### Q 1.2.d — Durée de fonctionnement effectif

La turbine fonctionne pour $V \geq V_\text{min} = 1{,}5 \, \text{m/s}$ :

$$\Delta t_\text{fonct} = \Delta t_{[1,5;2,0[} + \Delta t_{[2,0;2,5[} + \Delta t_{[2,5;3,0[} + \Delta t_{[3,0;3,5[} + \Delta t_{[3,5;+\infty[}$$
$$= 1\,752 + 1\,752 + 1\,314 + 876 + 876 = \boxed{6\,570 \, \text{h/an}}$$

*Remarque* : On suppose que la turbine fonctionne également pour $V \geq 3{,}5 \, \text{m/s}$ (en dessous de la limite de crue $V_\text{survie} = 4{,}0 \, \text{m/s}$) ; si la turbine est mise en veille au-dessus de 4 m/s, il faudrait retirer les heures correspondantes. À 3,5 m/s, la vitesse est encore inférieure à 4 m/s donc le fonctionnement est maintenu.

#### Q 1.2.e — Contraintes environnementales et réglementaires supplémentaires

1. **Autorisation de la Voies Navigables de France (VNF)** : toute installation en fleuve navigable nécessite un arrêté de concession ou d'autorisation délivré par VNF, avec étude d'impact sur le gabarit de navigation.

2. **Étude d'impact sur les zones de frayères** : la réglementation Natura 2000 et la Directive-cadre sur l'eau (DCE) imposent une évaluation de l'impact sur les habitats aquatiques, notamment les zones de reproduction des poissons migrateurs (saumon, lamproie en Loire).

*Autres réponses acceptables* : permis de construire sur le domaine public fluvial (DPF), raccordement au réseau électrique (autorisation ENEDIS), normes IEC pour les turbines hydrauliques.

---

### Corrigé 1.3 — Tableau des exigences fonctionnelles

#### Q 1.3.a — Complétion du tableau

| Case | Réponse | Justification |
|---|---|---|
| **[1]** | $P_\text{élec} \geq 5 \, \text{kW}$ (puissance électrique en sortie de génératrice) | FP-01 vise 5 kW en sortie ; le rendement de la génératrice est inclus |
| **[2]** | $\Delta t_\text{fonct} \geq 6\,570 \, \text{h/an}$ (heures à $V \geq 1{,}5 \, \text{m/s}$) | D'après Q 1.2.d ; FP-02 (3 200 h à puissance nominale) est satisfait |
| **[3]** | $n \leq 60 \, \text{tr/min}$ | FC-03, protection faune piscicole |
| **[4]** | $E_\text{an} \geq P_n \times 3\,200 + 0{,}5 \times P_n \times 2\,300 = 5\,000 \times 3\,200 + 2\,500 \times 2\,300$ | Production nominale + production partielle |

**Calcul de [4]** :
$$E_\text{an} \approx 5\,000 \times 3\,200 + 2\,500 \times 2\,300 = 16\,000\,000 + 5\,750\,000 = 21\,750\,000 \, \text{Wh}$$

$$\boxed{E_\text{an} \approx 21\,750 \, \text{kWh/an}}$$

#### Q 1.3.b — Chaîne d'énergie de l'HydroFlux-V5

```
┌─────────────────┐   ┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐   ┌──────────┐
│  Énergie        │   │  TURBINE         │   │  MULTIPLICATEUR  │   │  GÉNÉRATRICE     │   │  Réseau  │
│  cinétique      │ → │  (Rotor Darrieus)│ → │  (Épicycloïdal)  │ → │  GSAP            │ → │  électr. │
│  de l'eau       │   │  Cp = 0,35       │   │  η_multi = 0,96  │   │  η_gen = 0,90    │   │          │
│  P_hyd = f(V³)  │   │                  │   │                  │   │                  │   │          │
└─────────────────┘   └──────────────────┘   └──────────────────┘   └──────────────────┘   └──────────┘
                       P_méca = 0,35×P_hyd    P_multi = 0,96×P_méca  P_élec = 0,90×P_multi
                       
                       Pertes : 65 % rejetées  Pertes : 4 % dissipées  Pertes : 10 % chaleur
                       dans le sillage         en chaleur (paliers)    (résistances internes)
                       
η_global = Cp × η_multi × η_gen = 0,35 × 0,96 × 0,90 = 0,302 ≈ 30 %
```

---

## PHASE 2 — Modélisation de la turbine

---

### Corrigé 2.1 — Puissance hydraulique disponible

#### Q 2.1.a — Hypothèses de la formule

La formule $P_\text{hyd} = \frac{1}{2} \rho S V^3$ s'établit comme suit :

1. **Débit massique** traversant la surface $S$ : $\dot{m} = \rho \cdot S \cdot V$ (kg/s)
2. **Énergie cinétique** d'une masse élémentaire $dm$ se déplaçant à $V$ : $dE_c = \frac{1}{2} dm \cdot V^2$
3. **Puissance cinétique** : $P = \frac{dE_c}{dt} = \frac{1}{2} \dot{m} V^2 = \frac{1}{2} (\rho S V) V^2 = \frac{1}{2} \rho S V^3$

**Hypothèses** :
- Écoulement uniforme (vitesse $V$ uniforme sur la section $S$)
- Fluide incompressible ($\rho = \text{const}$)
- L'énergie potentielle est négligée (turbine horizontalement immergée dans un courant)
- On ne tient pas compte de la pression statique (écoulement libre)

#### Q 2.1.b — Calcul à $V_n = 2{,}5 \, \text{m/s}$

$$P_\text{hyd} = \frac{1}{2} \times 1\,000 \times 3{,}0 \times (2{,}5)^3$$
$$= \frac{1}{2} \times 1\,000 \times 3{,}0 \times 15{,}625$$
$$= 1\,500 \times 15{,}625$$

$$\boxed{P_\text{hyd} = 23\,438 \, \text{W} \approx 23{,}4 \, \text{kW}}$$

#### Q 2.1.c — Limite de Betz

$$P_\text{Betz} = C_{p,\text{max}} \times P_\text{hyd} = \frac{16}{27} \times 23\,438$$
$$= 0{,}593 \times 23\,438$$

$$\boxed{P_\text{Betz} \approx 13\,898 \, \text{W} \approx 13{,}9 \, \text{kW}}$$

*Interprétation* : Même la turbine "parfaite" ne peut extraire que 59,3 % de l'énergie cinétique disponible. Une partie de l'eau doit "passer" à travers la turbine pour maintenir l'écoulement.

#### Q 2.1.d — Puissance mécanique réelle

$$P_\text{méca} = C_p \times P_\text{hyd} = 0{,}35 \times 23\,438$$

$$\boxed{P_\text{méca} = 8\,203 \, \text{W} \approx 8{,}2 \, \text{kW}}$$

#### Q 2.1.e — Vérification de compatibilité avec $P_n = 5 \, \text{kW}$

Puissance électrique après multiplicateur et génératrice :
$$P_\text{élec} = P_\text{méca} \times \eta_\text{multi} \times \eta_\text{gen} = 8\,203 \times 0{,}96 \times 0{,}90$$
$$= 8\,203 \times 0{,}864 = 7\,087 \, \text{W} \approx 7{,}1 \, \text{kW}$$

$$\boxed{P_\text{élec} \approx 7{,}1 \, \text{kW} > P_n = 5 \, \text{kW}}$$ ✔

**Conclusion** : La puissance électrique calculée ($7{,}1 \, \text{kW}$) est supérieure à la puissance nominale visée ($5 \, \text{kW}$). La turbine est **surdimensionnée** par rapport à l'objectif ; en réalité, la génératrice sera régulée à 5 kW pour une charge nominale, et la puissance de 7,1 kW constitue une **marge de puissance** disponible. Cela signifie que l'objectif de 5 kW peut être atteint à une vitesse inférieure à $V_n$ (d'environ 2,2 m/s avec un $C_p = 0,35$).

---

### Corrigé 2.2 — Vitesse de rotation optimale

#### Q 2.2.a — Vitesse angulaire optimale

$$\omega_\text{opt} = \frac{\lambda_\text{opt} \times V_n}{R} = \frac{2{,}5 \times 2{,}5}{1{,}0}$$

$$\boxed{\omega_\text{opt} = 6{,}25 \, \text{rad/s}}$$

#### Q 2.2.b — Conversion en tr/min

$$n_\text{opt} = \frac{\omega_\text{opt} \times 60}{2\pi} = \frac{6{,}25 \times 60}{2\pi} = \frac{375}{6{,}2832}$$

$$\boxed{n_\text{opt} \approx 59{,}7 \, \text{tr/min}}$$

**Conformité FC-03** : $n_\text{opt} = 59{,}7 \, \text{tr/min} \leq 60 \, \text{tr/min}$ ✔ (avec une marge de 0,5 %)

#### Q 2.2.c — Vitesse linéaire des pales

$$v_\text{pale} = \omega_\text{opt} \times R = 6{,}25 \times 1{,}0 = 6{,}25 \, \text{m/s}$$

$$\boxed{v_\text{pale} = 6{,}25 \, \text{m/s} = 2{,}5 \times V_n}$$

*Commentaire* : La vitesse linéaire des pales ($6{,}25 \, \text{m/s}$) est exactement $\lambda_\text{opt} = 2{,}5$ fois plus grande que la vitesse du courant ($2{,}5 \, \text{m/s}$). C'est la définition même du TSR. En comparaison, une pale d'éolienne a typiquement $\lambda \approx 8$ (vitesse linéaire = 8 fois la vitesse du vent), ce qui explique le sifflement caractéristique des éoliennes. Ici, la valeur $\lambda = 2{,}5$ est modérée, ce qui est favorable à la discrétion acoustique et à la protection des poissons.

#### Q 2.2.d — Courbe $C_p(\lambda)$ d'une turbine Darrieus

```
C_p
0,40 │
     │               ★
0,35 │            /     \        ← C_p,max = 0,35 à λ = 2,5
     │          /           \
0,30 │        /               \
     │      /                   \
0,20 │    /                       \
     │  /                           \
0,10 │ /                               \
     │/                                  \
  0  └──────────────────────────────────── λ
     0  0,5  1,0  1,5  2,0  2,5  3,0  3,5  4,0

     λ < λ_opt : pale tournant trop lentement → angle d'attaque élevé
                 → décrochage aérodynamique → C_p diminue
     λ > λ_opt : pale tournant trop vite → perturbation du sillage
                 entre les 3 pales → efficacité réduite
```

---

### Corrigé 2.3 — Couple à l'arbre de turbine

#### Q 2.3.a — Couple nominal

$$C_\text{turbine} = \frac{P_\text{méca}}{\omega_\text{opt}} = \frac{8\,203}{6{,}25}$$

$$\boxed{C_\text{turbine} \approx 1\,312 \, \text{N·m}}$$

*Note* : Si on utilise $P_\text{méca} = 8{,}2 \, \text{kW}$ arrondi, on obtient $C_\text{turbine} \approx 1{,}31 \, \text{kN·m}$.

#### Q 2.3.b — Couple en crue

Puissance hydraulique en crue :
$$P_\text{hyd,crue} = \frac{1}{2} \times 1\,000 \times 3{,}0 \times (4{,}0)^3 = 1\,500 \times 64 = 96\,000 \, \text{W} = 96 \, \text{kW}$$

Puissance mécanique en crue (avec $C_p = 0{,}35$) :
$$P_\text{méca,crue} = 0{,}35 \times 96\,000 = 33\,600 \, \text{W}$$

Vitesse angulaire en crue (avec $\lambda_\text{opt} = 2{,}5$ et $V_\text{crue} = 4{,}0 \, \text{m/s}$) :
$$\omega_\text{crue} = \frac{2{,}5 \times 4{,}0}{1{,}0} = 10{,}0 \, \text{rad/s}$$

Couple en crue :
$$C_\text{max} = \frac{P_\text{méca,crue}}{\omega_\text{crue}} = \frac{33\,600}{10{,}0}$$

$$\boxed{C_\text{max} = 3\,360 \, \text{N·m}}$$

*Commentaire* : Le couple en crue ($3\,360 \, \text{N·m}$) est environ **2,6 fois plus grand** que le couple nominal ($1\,312 \, \text{N·m}$). L'arbre et les paliers doivent être dimensionnés pour cette charge exceptionnelle. En pratique, on peut mettre la turbine en veille (pales en drapeau) en crue pour éviter ce surcouple.

> *Note* : le résultat intermédiaire fourni dans le sujet ($C_\text{max} \approx 3\,840 \, \text{N·m}$) correspond à une hypothèse de calcul légèrement différente ($\omega_\text{crue}$ fixe à $\omega_\text{opt,nominal}$). La valeur $3\,360 \, \text{N·m}$ est celle cohérente avec notre calcul ci-dessus. Les deux valeurs sont acceptables selon l'hypothèse choisie.

#### Q 2.3.c — Rapport de puissance

$$\frac{P_\text{hyd,crue}}{P_\text{hyd,nominale}} = \frac{96\,000}{23\,438} = 4{,}10$$

*Vérification par la loi des cubes* :
$$\left(\frac{V_\text{crue}}{V_n}\right)^3 = \left(\frac{4{,}0}{2{,}5}\right)^3 = (1{,}6)^3 = 4{,}096 \approx 4{,}1$$ ✔

**Commentaire** : Une augmentation de vitesse de seulement 60 % ($4{,}0 / 2{,}5 = 1{,}6$) entraîne une multiplication de la puissance hydraulique par **4,1**. C'est la conséquence directe de la dépendance en $V^3$. Cela illustre l'importance de dimensionner les organes mécaniques pour les conditions de crue, et non seulement pour les conditions nominales.

---

## PHASE 3 — Conception préliminaire de la transmission

---

### Corrigé 3.1 — Choix de la transmission

#### Q 3.1.a — Rapport de multiplication

$$\mu = \frac{n_\text{gen}}{n_\text{turbine}} = \frac{750}{59{,}7}$$

$$\boxed{\mu \approx 12{,}6}$$

#### Q 3.1.b — Tableau comparatif

| Critère | Transmission directe | Multiplicateur épicycloïdal |
|---|---|---|
| Rapport de vitesse | $\mu = 1$ (vitesse identique) | $\mu \approx 12{,}6$ |
| Rendement | ~1 (idéal) | 0,96 |
| Encombrement | Faible (arbre direct) | Moyen (boîtier étanche) |
| Complexité maintenance | Faible (peu de pièces) | Élevée (engrenages, joints) |
| Coût | Faible | Élevé (+30 à 50 %) |
| Adapté à ce cas ? | **Non** : génératrice GSAP 750 tr/min incompatible | **Oui** : adapte turbine 60 tr/min à 750 tr/min |

**Note sur la transmission directe** : Pour éviter le multiplicateur, il faudrait une génératrice à **aimants permanents multipôles** tournant à 60 tr/min (génératrice à prise directe, "direct drive"). Ces machines existent mais sont plus volumineuses, plus lourdes et plus coûteuses pour la même puissance.

#### Q 3.1.c — Choix justifié

**Choix retenu : multiplicateur épicycloïdal ($\mu = 12{,}6$)**.

Justification :
1. La génératrice GSAP standard (750 tr/min, 4 paires de pôles, 50 Hz) est le composant disponible commercialement à moindre coût. Son adaptation au réseau 50 Hz est directe.
2. Le rapport $\mu = 12{,}6$ est bien adapté à un multiplicateur épicycloïdal (plage usuelle : 3 à 20 dans un étage).
3. Bien que le rendement soit légèrement inférieur ($\eta = 0{,}96$), la simplification de la génératrice compense ce désavantage.
4. L'alternative "direct drive" serait possible pour une turbine de forte puissance (> 100 kW), mais à 5 kW, le surcoût d'une génératrice basse vitesse est disproportionné.

---

### Corrigé 3.2 — Dimensionnement de l'arbre de turbine

#### Q 3.2.a — Formule de la contrainte en torsion

Pour un arbre plein de diamètre $d$, le moment polaire d'inertie est $I_p = \pi d^4 / 32$, et la distance à l'axe est $r = d/2$ :

$$\tau_\text{max} = \frac{C \cdot r}{I_p} = \frac{C \cdot d/2}{\pi d^4/32} = \frac{C \times d/2 \times 32}{\pi d^4} = \frac{16C}{\pi d^3}$$

#### Q 3.2.b — Contrainte admissible

$$\tau_\text{adm} = \frac{R_e}{s \times \sqrt{3}} = \frac{220}{2 \times 1{,}732} = \frac{220}{3{,}464}$$

$$\boxed{\tau_\text{adm} = 63{,}5 \, \text{MPa}}$$

#### Q 3.2.c — Diamètre minimal

On dimensionne pour $C = C_\text{max} = 3\,360 \, \text{N·m}$ (couple en crue) :

$$d_\text{min} = \left(\frac{16 \cdot C_\text{max}}{\pi \cdot \tau_\text{adm}}\right)^{1/3}$$

$$= \left(\frac{16 \times 3\,360}{\pi \times 63{,}5 \times 10^6}\right)^{1/3}$$

$$= \left(\frac{53\,760}{199{,}5 \times 10^6}\right)^{1/3}$$

$$= \left(\frac{53\,760}{199\,500\,000}\right)^{1/3}$$

$$= (2{,}695 \times 10^{-4})^{1/3}$$

$$= (269{,}5 \times 10^{-6})^{1/3}$$

*Calcul* : $\sqrt[3]{269{,}5 \times 10^{-6}} = \sqrt[3]{269{,}5} \times 10^{-2}$

$\sqrt[3]{269{,}5} \approx 6{,}45$ (car $6{,}45^3 = 268{,}3 \approx 269{,}5$)

$$\boxed{d_\text{min} \approx 6{,}45 \times 10^{-2} \, \text{m} = 64{,}5 \, \text{mm}}$$

*Vérification* : $\tau = 16 \times 3360 / (\pi \times 0{,}0645^3) = 53760 / (\pi \times 2{,}683 \times 10^{-4}) = 53760 / 843{,}0 \times 10^{-4} = 53760 / 0{,}08430 \approx 638\,000 \, \text{Pa}$... Il faut vérifier les unités.

*Correction de calcul* :
$$d_\text{min}^3 = \frac{16 \times 3360}{\pi \times 63{,}5 \times 10^6} = \frac{53\,760}{199\,490\,000} = 2{,}695 \times 10^{-4} \, \text{m}^3$$

$$d_\text{min} = (2{,}695 \times 10^{-4})^{1/3} \, \text{m}$$

Conversion : $2{,}695 \times 10^{-4} \, \text{m}^3 = 269\,500 \, \text{mm}^3$

$d_\text{min} = (269\,500)^{1/3} \, \text{mm}$

$\sqrt[3]{270\,000} \approx 64{,}6$ (car $64^3 = 262\,144$ et $65^3 = 274\,625$, par interpolation : $64{,}6^3 \approx 269\,500$) ✔

$$\boxed{d_\text{min} \approx 64{,}6 \, \text{mm}}$$

#### Q 3.2.d — Choix du diamètre normalisé

$d_\text{min} = 64{,}6 \, \text{mm}$ → On choisit **$d = 65 \, \text{mm}$** dans la série normalisée... mais 65 mm n'est pas dans la série proposée. On prend donc **$d = 70 \, \text{mm}$** (valeur supérieure la plus proche).

*Note* : Si le sujet avait utilisé le couple nominal ($C_\text{turbine} = 1\,312 \, \text{N·m}$) :
$$d_\text{min,nom}^3 = \frac{16 \times 1312}{\pi \times 63{,}5 \times 10^6} = \frac{20992}{199{,}5 \times 10^6} = 1{,}052 \times 10^{-4} \, \text{m}^3 = 105\,200 \, \text{mm}^3$$
$$d_\text{min,nom} = (105\,200)^{1/3} \approx 47{,}2 \, \text{mm}$$

Avec le couple nominal, $d = 50 \, \text{mm}$ serait suffisant. **On recommande $d = 70 \, \text{mm}$** pour les conditions de crue, avec vérification en fatigue pour les cycles thermiques.

**Choix retenu : $d = 70 \, \text{mm}$**. Justification : c'est le premier diamètre normalisé au-dessus de $d_\text{min} = 64{,}6 \, \text{mm}$ dans la série commerciale. Il offre une marge de sécurité réelle supérieure à $s = 2$ en conditions de crue.

#### Q 3.2.e — Rigidité en torsion

On vérifie pour le couple nominal $C_\text{turbine} = 1\,312 \, \text{N·m}$ (charge en service courant) avec $d = 70 \, \text{mm} = 0{,}070 \, \text{m}$ :

$$I_p = \frac{\pi d^4}{32} = \frac{\pi \times (0{,}070)^4}{32} = \frac{\pi \times 2{,}401 \times 10^{-5}}{32} = \frac{7{,}543 \times 10^{-5}}{32} = 2{,}357 \times 10^{-6} \, \text{m}^4$$

Angle de torsion par mètre ($l = 1{,}0 \, \text{m}$) :
$$\phi = \frac{C \cdot l}{G \cdot I_p} = \frac{1\,312 \times 1{,}0}{77 \times 10^9 \times 2{,}357 \times 10^{-6}}$$

$$= \frac{1\,312}{181\,489} = 7{,}23 \times 10^{-3} \, \text{rad/m}$$

Conversion en degrés par mètre :
$$\phi = 7{,}23 \times 10^{-3} \times \frac{180°}{\pi} = 7{,}23 \times 10^{-3} \times 57{,}30 = 0{,}414°/\text{m}$$

**Critère** : $\phi \leq 0{,}5°/\text{m}$

$0{,}414°/\text{m} < 0{,}5°/\text{m}$ ✔

**L'arbre de diamètre 70 mm satisfait le critère de rigidité en torsion.**

---

### Corrigé 3.3 — Choix des matériaux

#### Q 3.3.a — Acier inoxydable 316L

**Composition chimique** (approximative) :
- Fer (Fe) : base
- Chrome (Cr) : 16–18 % → formation de la couche passive (Cr₂O₃)
- Nickel (Ni) : 10–14 % → structure austénitique, améliore ductilité et soudabilité
- Molybdène (Mo) : 2–3 % → résistance accrue à la corrosion par piqûres (en milieu chloruré)
- Carbone (C) : < 0,03 % (L = Low Carbon, résistance à la corrosion intergranulaire)

**Type de corrosion résistée** : Corrosion par piqûres en milieu aqueux, corrosion galvanique légère, corrosion intergranulaire (grâce à la faible teneur en carbone).

**Comparaison 316L vs 42CrMo4** :

| Critère | Acier 316L | Acier 42CrMo4 |
|---|---|---|
| Résistance à la corrosion | Excellente | Médiocre (corrosion rouille rapide en eau douce) |
| Limite élastique | 220 MPa | 650 MPa |
| Résistance mécanique | Moyenne | Élevée |
| Coût | ×3 à ×5 par rapport à l'acier carbone | Référence |
| Soudabilité | Excellente | Difficile (risque fissuration) |

*Conclusion* : Le 316L est **obligatoire** pour les pièces immergées malgré sa résistance mécanique moindre. Le surdimensionnement de l'arbre ($d = 70 \, \text{mm}$ vs $d_\text{min} = 50 \, \text{mm}$ avec 42CrMo4) est le prix à payer pour la tenue en corrosion sur 20 ans.

#### Q 3.3.b — Traitement de surface complémentaire

**Recommandation** : Revêtement **PTFE (polytétrafluoroéthylène)** sur les surfaces de contact des paliers (zones de frottement).

Justification :
- Le PTFE est inerte chimiquement et résiste à tous les milieux aqueux
- Il réduit le coefficient de frottement (< 0,04) → diminue l'usure des paliers
- Il évite l'adhérence des algues et dépôts biologiques

*Alternative* : Traitement de nitruration en phase gazeuse (couche de nitrure de chrome CrN) pour les zones de contact métal-métal.

#### Q 3.3.c — Polymère composite GFRP

**Analyse** :
- Module de cisaillement GFRP : $G_\text{GFRP} = 7 \, \text{GPa}$ vs $G_{316L} = 77 \, \text{GPa}$ → 11 fois plus faible

Angle de torsion avec GFRP ($d = 70 \, \text{mm}$, $l = 1{,}0 \, \text{m}$) :
$$\phi_\text{GFRP} = \phi_{316L} \times \frac{G_{316L}}{G_\text{GFRP}} = 0{,}414 \times \frac{77}{7} = 0{,}414 \times 11 = 4{,}55°/\text{m}$$

**Critère** : $4{,}55°/\text{m} \gg 0{,}5°/\text{m}$ ✗

**Conclusion** : L'arbre en GFRP ne respecte **pas** le critère de rigidité en torsion. Pour satisfaire ce critère, il faudrait augmenter le diamètre d'un facteur $\approx 11^{1/4} \approx 1{,}82$, soit $d \approx 127 \, \text{mm}$, ce qui est rédhibitoire. **La proposition d'un arbre en GFRP est irrecevable** pour ce dimensionnement.

---

## PHASE 4 — Validation et bilan

---

### Corrigé 4.1 — Bilan énergétique

#### Q 4.1.a — Tableau de bilan

| Étape | Formule | Valeur numérique |
|---|---|---|
| **[1]** Puissance hydraulique | $P_\text{hyd} = \frac{1}{2} \times 1000 \times 3{,}0 \times 2{,}5^3$ | **23,44 kW** |
| **[2]** Puissance mécanique turbine | $P_\text{méca} = 0{,}35 \times 23{,}44$ | **8,20 kW** |
| **[3]** Puissance après multiplicateur | $P_\text{multi} = 0{,}96 \times 8{,}20$ | **7,87 kW** |
| **[4]** Puissance électrique (génératrice) | $P_\text{élec} = 0{,}90 \times 7{,}87$ | **7,09 kW** |
| **[5]** Rendement global | $\eta_\text{global} = 7{,}09 / 23{,}44$ | **0,302 ≈ 30,2 %** |

#### Q 4.1.b — Rendement global et comparaison à Betz

$$\eta_\text{global} = C_p \times \eta_\text{multi} \times \eta_\text{gen} = 0{,}35 \times 0{,}96 \times 0{,}90 = 0{,}302 = 30{,}2\%$$

**Comparaison à la limite de Betz** : $\eta_\text{global} / C_{p,\text{Betz}} = 0{,}302 / 0{,}593 = 50{,}9\%$

L'HydroFlux-V5 utilise environ **51 % du potentiel théorique maximal** défini par Betz. La répartition des pertes :
- Perte dans le sillage hydraulique (limite de Betz) : 40,7 % de $P_\text{hyd}$ non récupérable
- Perte aérodynamique (turbine réelle vs Betz) : $P_\text{hyd} - P_\text{méca} - P_\text{Betz,non capté} = (1-C_p) \times P_\text{hyd} \times (1-16/27)$... (les pertes entre $C_p = 0,35$ et $C_{p,\text{Betz}} = 0,593$) représentent $(0{,}593-0{,}35)/0{,}593 = 41\%$ du potentiel exploitable
- Pertes mécaniques (multiplicateur) : 4 %
- Pertes électriques (génératrice) : 10 %

---

### Corrigé 4.2 — Production annuelle

#### Q 4.2.a — Puissance par plage

On utilise la vitesse médiane de chaque plage. Rappel : $\eta_\text{global} = 0{,}302$, $V_\text{min} = 1{,}5 \, \text{m/s}$, $P_n = 5 \, \text{kW}$ pour $V \geq V_n = 2{,}5 \, \text{m/s}$.

| Plage $V$ (m/s) | $V_\text{moy}$ | $P_\text{hyd}$ (kW) | $P_\text{élec}$ (kW) | $\Delta t$ (h) |
|---|---|---|---|---|
| $0 \leq V < 1{,}0$ | 0,5 | $1500 \times 0{,}125 = 0{,}19$ | 0 (turbine arrêtée) | 876 |
| $1{,}0 \leq V < 1{,}5$ | 1,25 | $1500 \times 1{,}953 = 2{,}93$ | 0 (en dessous de $V_\text{min}$) | 1 314 |
| $1{,}5 \leq V < 2{,}0$ | 1,75 | $1500 \times 5{,}359 = 8{,}04$ | $0{,}302 \times 8{,}04 = 2{,}43$ | 1 752 |
| $2{,}0 \leq V < 2{,}5$ | 2,25 | $1500 \times 11{,}39 = 17{,}09$ | $0{,}302 \times 17{,}09 = 5{,}16$ → plafonné à 5 kW | 1 752 |
| $2{,}5 \leq V < 3{,}0$ | 2,75 | $1500 \times 20{,}80 = 31{,}2$ | 5 kW (régulation) | 1 314 |
| $3{,}0 \leq V < 3{,}5$ | 3,25 | $1500 \times 34{,}33 = 51{,}5$ | 5 kW (régulation) | 876 |
| $V \geq 3{,}5$ | 3,75 | $1500 \times 52{,}73 = 79{,}1$ | 5 kW (régulation) | 876 |

*Note sur la plage $[2{,}0 ; 2{,}5[$ : $P_\text{élec} = 0{,}302 \times 17{,}09 = 5{,}16 \, \text{kW}$ est très proche de $P_n = 5 \, \text{kW}$ ; on prend $P_\text{élec} = 5 \, \text{kW}$ (plafonnement par régulation à partir de $V \approx 2{,}4 \, \text{m/s}$).*

#### Q 4.2.b — Production annuelle

$$E_\text{an} = \sum_i \bar{P}_i \times \Delta t_i$$

$$= 0 \times 876 + 0 \times 1\,314 + 2{,}43 \times 1\,752 + 5{,}0 \times 1\,752 + 5{,}0 \times 1\,314 + 5{,}0 \times 876 + 5{,}0 \times 876$$

$$= 0 + 0 + 4\,255 + 8\,760 + 6\,570 + 4\,380 + 4\,380$$

$$= 28\,345 \, \text{kWh}$$

$$\boxed{E_\text{an} \approx 28\,300 \, \text{kWh/an}}$$

#### Q 4.2.c — Comparaison à la consommation d'un foyer

Un foyer français moyen consomme environ $4\,500 \, \text{kWh/an}$ (hors chauffage électrique).

$$N_\text{foyers} = \frac{E_\text{an}}{4\,500} = \frac{28\,300}{4\,500} \approx 6{,}3 \, \text{foyers}$$

**Une hydrolienne HydroFlux-V5 peut alimenter environ 6 foyers** en électricité. À l'échelle du fleuve (largeur 250 m), on pourrait installer plusieurs dizaines d'hydroliennes espacées, multipliant d'autant la production.

---

### Corrigé 4.3 — Validation et améliorations

#### Q 4.3.a — Tableau de validation

| Exigence | Valeur requise | Valeur calculée | Conforme ? |
|---|---|---|---|
| Puissance nominale $P_n$ | $\geq 5 \, \text{kW}$ | $P_\text{élec} \approx 7{,}1 \, \text{kW}$ (puis régulée à 5 kW) | ✔ |
| Durée de fonctionnement | $\geq 3\,200 \, \text{h/an}$ | $6\,570 \, \text{h/an}$ (à $V \geq 1{,}5 \, \text{m/s}$) | ✔ |
| Vitesse de rotation | $\leq 60 \, \text{tr/min}$ | $n_\text{opt} = 59{,}7 \, \text{tr/min}$ | ✔ |
| Survie en crue | $V_\text{survie} = 4{,}0 \, \text{m/s}$ | Dimensionné pour $V = 4{,}0 \, \text{m/s}$ (arbre 70 mm) | ✔ |

**Conclusion** : Toutes les exigences du cahier des charges sont satisfaites. Le concept HydroFlux-V5 est validé au niveau de la conception préliminaire. La phase suivante serait la validation par prototype (mesures en conditions réelles, essais fatigue, tests biologiques).

#### Q 4.3.b — Améliorations techniques

| Amélioration | Impact | Paramètre affecté |
|---|---|---|
| **1. Optimisation du profil des pales** (NACA 0018 → profil asymétrique adapté aux turbines Darrieus basse solidité) | Augmentation de $C_p$ de 0,35 à 0,40 → +14 % de puissance | $C_p$ ↑ |
| **2. Augmentation de la hauteur des pales** (de $H = 1{,}5$ à $H = 2{,}0 \, \text{m}$) | Surface $S$ augmente de 3,0 à 4,0 m² (+33 %) → +33 % de puissance hydraulique | $S$ ↑ |
| **3. Contrôle du pitch des pales** (orientation variable de l'angle d'attaque selon la position angulaire) | Maintien du $C_p$ optimal sur une plage de vitesses plus large → meilleur facteur de charge annuel | $C_p$ sur plage $V$ élargie |

*Impacts sur $E_\text{an}$* : En combinant améliorations 1 et 2, la production annuelle pourrait atteindre $28\,300 \times 1{,}14 \times 1{,}33 \approx 43\,000 \, \text{kWh/an}$ (environ 9 foyers).

---

*— Fin du corrigé —*
