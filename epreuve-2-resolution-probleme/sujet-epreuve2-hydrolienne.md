# CAPET SII — Ingénierie Mécanique — Session 2026
## Épreuve 2 : Résolution de problème
### Durée : 4 heures — Coefficient 2 — Note sur 20

---

> **Document d'entraînement non officiel — Usage pédagogique exclusivement**

---

## Instructions générales

- Le sujet est composé de **quatre phases progressives** ; elles doivent être traitées dans l'ordre.
- Les phases sont partiellement indépendantes : il est possible de passer à une phase suivante même si la précédente est incomplète, en utilisant les résultats intermédiaires fournis le cas échéant.
- La qualité de la **démarche de résolution** est valorisée autant que le résultat final.
- Des **résultats intermédiaires** sont parfois fournis dans le texte (encadrés en gris) pour permettre la progression ; leur utilisation est autorisée même si le candidat ne les a pas établis.
- **Calculatrice non programmable** autorisée.
- Constantes utiles : $g = 9{,}81 \, \text{m/s}^2$, $\rho_\text{eau} = 1000 \, \text{kg/m}^3$, $\pi \approx 3{,}1416$.

---

## Présentation du système — Hydrolienne fluviale HydroFlux-V5

### Contexte — Transition énergétique et hydrocinétique fluviale

La transition énergétique impose d'exploiter des sources d'énergie renouvelables décentralisées. Les fleuves et rivières français représentent un **potentiel hydrocinétique inexploité** considérable : des milliers de kilomètres de cours d'eau présentent des courants permanents compris entre 1 et 4 m/s, sans nécessiter de barrage ni d'infrastructure lourde.

L'**hydrolienne fluviale** (ou turbine hydrocinétique) exploite l'**énergie cinétique** de l'eau en mouvement, à la manière d'une éolienne dans l'eau. Elle ne nécessite pas de chute d'eau (contrairement aux turbines hydrauliques classiques), ce qui la rend adaptable à des sites fluviaux de profondeur modérée.

La société fictive **FluvEnergy** a développé l'**HydroFlux-V5**, une hydrolienne à **axe vertical** de type **Darrieus**, immergée dans un fleuve. Ce type de turbine présente l'avantage de fonctionner quel que soit le sens du courant dans le plan horizontal, et de loger la génératrice en position émergée ou immergée dans un boîtier étanche.

### Description technique de l'HydroFlux-V5

**Figure 1 — Vue de dessus de l'HydroFlux-V5** *(voir fichier schemas-descriptions.md)*

L'HydroFlux-V5 est composée de :
- Un **rotor à 3 pales profilées** NACA 0018 disposées à 120° sur un cercle de rayon $R = 1{,}0 \, \text{m}$
- Un **arbre central vertical** reliant le rotor à la génératrice
- Une **génératrice synchrone à aimants permanents** (GSAP) immergée
- Un **système d'ancrage** au fond du fleuve (câbles et massif béton)
- Un **câble électrique** sous-marin vers la rive

#### Caractéristiques techniques

| Paramètre | Symbole | Valeur |
|---|---|---|
| Rayon du rotor | $R$ | $1{,}0 \, \text{m}$ |
| Diamètre du rotor | $D = 2R$ | $2{,}0 \, \text{m}$ |
| Hauteur des pales | $H$ | $1{,}5 \, \text{m}$ |
| Surface de capture (projetée) | $S = D \times H$ | $3{,}0 \, \text{m}^2$ |
| Vitesse nominale du courant | $V_n$ | $2{,}5 \, \text{m/s}$ |
| Puissance nominale visée | $P_n$ | $5 \, \text{kW}$ |
| Coefficient de puissance (rendement turbine) | $C_p$ | $0{,}35$ |
| Masse volumique de l'eau | $\rho$ | $1\,000 \, \text{kg/m}^3$ |
| Profondeur d'immersion minimale | — | $3 \, \text{m}$ |
| Durée de vie visée | — | $20 \, \text{ans}$ |
| Rapport de vitesse spécifique optimal | $\lambda_\text{opt}$ | $2{,}5$ |
| Rendement du multiplicateur (si utilisé) | $\eta_\text{multi}$ | $0{,}96$ |
| Rendement de la génératrice | $\eta_\text{gen}$ | $0{,}90$ |

#### Données sur le site fluvial

Le site retenu est la **Loire à Montjean-sur-Loire** (données fictives mais réalistes) :

| Paramètre du site | Valeur |
|---|---|
| Largeur du chenal principal | 250 m |
| Profondeur moyenne | 4,5 m |
| Vitesse du courant (débit nominal) | 2,5 m/s |
| Vitesse du courant (étiage) | 1,2 m/s |
| Vitesse du courant (crue modérée) | 4,0 m/s |
| Durée annuelle à $V \geq V_n$ | 3 200 h/an |
| Durée annuelle à $V \geq 1{,}5 \, \text{m/s}$ | 5 500 h/an |
| Température de l'eau | 5°C à 22°C |

---

## PHASE 1 — Exploitation des ressources *(25 points)*

### Question 1.1 — Analyse du cahier des charges (8 points)

Le document ressource DR-1 ci-dessous présente un extrait du **cahier des charges fonctionnel** de l'HydroFlux-V5.

#### Document Ressource DR-1 — Extrait du CdCF

| Réf. | Fonction | Critère | Niveau | Observation |
|---|---|---|---|---|
| FP-01 | Convertir l'énergie cinétique du courant en énergie électrique | Puissance nominale | $P_n \geq 5 \, \text{kW}$ | À $V_n = 2{,}5 \, \text{m/s}$ |
| FP-02 | Fonctionner en continu | Durée de fonctionnement annuel | $\geq 3\,200 \, \text{h/an}$ | Hors maintenance |
| FC-01 | Ne pas perturber la navigation fluviale | Encombrement | Diamètre rotor $\leq 3 \, \text{m}$ | Arrêté préfectoral |
| FC-02 | Résister aux crues | Vitesse de courant maximale | Survie à $V_\text{crue} = 4{,}0 \, \text{m/s}$ | Rotor en veille, pales orientées |
| FC-03 | Respecter l'écologie fluviale | Impact faune piscicole | Vitesse de rotation $\leq 60 \, \text{tr/min}$ | Protection des poissons |
| FC-04 | Être maintenu facilement | Accès sans plongeur | Système levable depuis la rive | Interface de maintenance |
| FC-05 | Résister à la corrosion | Matériaux immergés | Acier inox 316L ou polymères composites | Durée 20 ans |

**Q 1.1.a** — Identifier la **fonction principale** et les **fonctions contraintes** du système HydroFlux-V5, en s'appuyant sur le document DR-1. Proposer un diagramme pieuvre simplifié (texte + schéma) identifiant les éléments du milieu extérieur. (3 points)

**Q 1.1.b** — La contrainte FC-03 impose $n \leq 60 \, \text{tr/min}$. En utilisant la relation entre vitesse angulaire et vitesse de rotation :

$$\omega = \frac{2\pi \cdot n}{60}$$

Calculer la vitesse angulaire maximale admissible $\omega_\text{max}$ en rad/s. (1 point)

**Q 1.1.c** — Le rapport de vitesse spécifique est défini par :

$$\lambda = \frac{\omega \cdot R}{V}$$

À la vitesse nominale $V_n = 2{,}5 \, \text{m/s}$ et avec $\omega_\text{max}$ calculé en Q 1.1.b, calculer $\lambda_\text{max}$ et comparer à $\lambda_\text{opt} = 2{,}5$. Que peut-on conclure sur la compatibilité entre la contrainte FC-03 et les performances nominales ? (2 points)

**Q 1.1.d** — Le document DR-1 cite la contrainte FC-05 (résistance à la corrosion). Identifier **deux mécanismes de corrosion** susceptibles d'affecter l'HydroFlux-V5 en milieu fluvial, et proposer pour chacun une solution technique. (2 points)

---

### Question 1.2 — Analyse des données hydrologiques (9 points)

#### Document Ressource DR-2 — Profil de vitesse annuel (données fictives)

Le profil hydrologique du site de Montjean-sur-Loire est modélisé par la **distribution de Weibull** de la vitesse du courant $V$ :

$$f(V) = \frac{k}{c} \left(\frac{V}{c}\right)^{k-1} \exp\left[-\left(\frac{V}{c}\right)^k\right]$$

avec les paramètres : $k = 2{,}2$ (facteur de forme), $c = 2{,}8 \, \text{m/s}$ (facteur d'échelle).

Pour simplifier les calculs, on utilisera la **table de distribution discrète** suivante :

| Plage de vitesse $V$ (m/s) | Durée annuelle $\Delta t$ (h/an) | Probabilité $P(V)$ |
|---|---|---|
| $0 \leq V < 1{,}0$ | 876 | 10 % |
| $1{,}0 \leq V < 1{,}5$ | 1\,314 | 15 % |
| $1{,}5 \leq V < 2{,}0$ | 1\,752 | 20 % |
| $2{,}0 \leq V < 2{,}5$ | 1\,752 | 20 % |
| $2{,}5 \leq V < 3{,}0$ | 1\,314 | 15 % |
| $3{,}0 \leq V < 3{,}5$ | 876 | 10 % |
| $V \geq 3{,}5$ | 876 | 10 % |
| **Total** | **8 760 h** | **100 %** |

**Q 1.2.a** — Vérifier que la somme des durées est cohérente avec le nombre d'heures dans une année (365 × 24). (1 point)

**Q 1.2.b** — D'après la table, calculer la durée annuelle totale pendant laquelle la vitesse est supérieure ou égale à la vitesse nominale $V_n = 2{,}5 \, \text{m/s}$. Comparer au cahier des charges (FP-02 : $\geq 3\,200 \, \text{h/an}$). (2 points)

**Q 1.2.c** — La puissance hydraulique disponible dans une tranche de courant de vitesse $V$ est :

$$P_\text{hyd}(V) = \frac{1}{2} \cdot \rho \cdot S \cdot V^3$$

Calculer $P_\text{hyd}$ pour $V = 1{,}5 \, \text{m/s}$, $V = 2{,}5 \, \text{m/s}$ et $V = 3{,}5 \, \text{m/s}$ avec $S = 3{,}0 \, \text{m}^2$. (3 points)

**Q 1.2.d** — La turbine cesse de fonctionner en dessous d'une vitesse de démarrage $V_\text{min} = 1{,}5 \, \text{m/s}$ (couple de démarrage insuffisant). D'après la table, quelle est la durée annuelle de fonctionnement effectif ? (1 point)

**Q 1.2.e** — Identifier **deux contraintes environnementales et réglementaires** liées à l'installation d'une hydrolienne en fleuve, en dehors de celles déjà mentionnées dans le CdCF. (2 points)

---

### Question 1.3 — Bilan des exigences fonctionnelles (8 points)

**Q 1.3.a** — Compléter le **tableau des exigences fonctionnelles** ci-dessous, en vous appuyant sur les documents DR-1 et DR-2 et vos réponses précédentes :

| ID | Exigence | Critère | Valeur cible | Source |
|---|---|---|---|---|
| EF-01 | Puissance nominale en sortie électrique | Puissance électrique aux bornes de la génératrice | **[1]** | CdCF FP-01 |
| EF-02 | Durée de fonctionnement annuel | Heures à $V \geq V_\text{min}$ | **[2]** | DR-2 |
| EF-03 | Vitesse de rotation maximale | Tours par minute | **[3]** | CdCF FC-03 |
| EF-04 | Production annuelle d'énergie | kWh/an | **[4]** | À estimer |
| EF-05 | Résistance à la crue | Vitesse de survie | $\leq 4{,}0 \, \text{m/s}$ | CdCF FC-02 |

Pour **[4]**, on peut estimer la production annuelle en supposant que la turbine fonctionne à sa puissance nominale $P_n = 5 \, \text{kW}$ pendant les 3 200 heures à $V \geq V_n$, et à 50 % de $P_n$ pendant les 2 300 heures restantes à $1{,}5 \leq V < 2{,}5 \, \text{m/s}$.

**Q 1.3.b** — Représenter schématiquement la **chaîne d'énergie** de l'HydroFlux-V5, depuis l'énergie cinétique de l'eau jusqu'au réseau électrique. Identifier les rendements à chaque étape. (4 points)

---

## PHASE 2 — Modélisation de la turbine *(30 points)*

### Question 2.1 — Puissance hydraulique disponible (10 points)

La **puissance hydraulique** (ou puissance cinétique) disponible dans un cylindre d'eau de section $S$ se déplaçant à la vitesse $V$ est donnée par :

$$\boxed{P_\text{hyd} = \frac{1}{2} \cdot \rho \cdot S \cdot V^3}$$

**Q 2.1.a** — Identifier les hypothèses physiques permettant d'établir cette formule à partir de la définition de l'énergie cinétique et du débit massique. (2 points)

**Q 2.1.b** — Calculer la puissance hydraulique disponible $P_\text{hyd}$ à la vitesse nominale $V_n = 2{,}5 \, \text{m/s}$ :

- Données : $\rho = 1\,000 \, \text{kg/m}^3$, $S = 3{,}0 \, \text{m}^2$, $V_n = 2{,}5 \, \text{m/s}$
- Exprimer le résultat en watts et en kilowatts (2 points)

**Q 2.1.c** — La **limite de Betz** (1919) établit que le rendement maximal théorique d'une turbine dans un fluide en écoulement est :

$$C_{p,\text{max}} = \frac{16}{27} \approx 0{,}593$$

En déduire la **puissance maximale théorique** $P_\text{Betz}$ que pourrait extraire l'HydroFlux-V5 à $V_n$. (2 points)

**Q 2.1.d** — En réalité, le coefficient de puissance de la turbine est $C_p = 0{,}35$. Calculer la **puissance mécanique réelle** $P_\text{méca}$ à la sortie du rotor :

$$P_\text{méca} = C_p \cdot P_\text{hyd}$$

(2 points)

**Q 2.1.e** — Vérifier si la puissance mécanique $P_\text{méca}$ est compatible avec la puissance nominale visée $P_n = 5 \, \text{kW}$ (en tenant compte des rendements du multiplicateur $\eta_\text{multi} = 0{,}96$ et de la génératrice $\eta_\text{gen} = 0{,}90$). (2 points)

---

### Question 2.2 — Vitesse de rotation optimale (10 points)

Le **rapport de vitesse spécifique** (ou Tip Speed Ratio, TSR) est le rapport entre la vitesse linéaire de l'extrémité des pales et la vitesse du courant :

$$\lambda = \frac{\omega \cdot R}{V}$$

Pour une turbine de type Darrieus, la valeur optimale est $\lambda_\text{opt} = 2{,}5$.

**Q 2.2.a** — Exprimer la vitesse angulaire optimale $\omega_\text{opt}$ en fonction de $\lambda_\text{opt}$, $R$ et $V$. Calculer $\omega_\text{opt}$ en rad/s à la vitesse nominale $V_n = 2{,}5 \, \text{m/s}$. (3 points)

**Q 2.2.b** — Convertir $\omega_\text{opt}$ en tours par minute $n_\text{opt}$ (tr/min). Vérifier la conformité avec la contrainte FC-03 ($n \leq 60 \, \text{tr/min}$). (3 points)

**Q 2.2.c** — Calculer la vitesse linéaire $v_\text{pale} = \omega_\text{opt} \cdot R$ à l'extrémité des pales. Commenter cette valeur en la comparant à la vitesse du courant $V_n$. (2 points)

**Q 2.2.d** — Tracer l'allure de $C_p$ en fonction de $\lambda$ pour une turbine Darrieus (forme de cloche avec maximum à $\lambda_\text{opt} = 2{,}5$ et $C_{p,\text{max}} = 0{,}35$). Décrire qualitativement le comportement pour $\lambda < \lambda_\text{opt}$ et $\lambda > \lambda_\text{opt}$. (2 points)

---

### Question 2.3 — Couple à l'arbre de turbine (10 points)

**Q 2.3.a** — Exprimer le **couple résistant** $C_\text{turbine}$ à l'arbre de la turbine en fonction de la puissance mécanique $P_\text{méca}$ et de la vitesse angulaire $\omega_\text{opt}$ :

$$C_\text{turbine} = \frac{P_\text{méca}}{\omega_\text{opt}}$$

Calculer numériquement $C_\text{turbine}$. (3 points)

**Q 2.3.b** — En régime de crue ($V_\text{crue} = 4{,}0 \, \text{m/s}$), calculer la puissance hydraulique $P_\text{hyd,crue}$ et le couple maximal $C_\text{max}$ à l'arbre (en supposant $C_p = 0{,}35$ constant). Commenter l'importance du dimensionnement en crue. (4 points)

**Q 2.3.c** — La puissance hydraulique varie avec $V^3$. Calculer le rapport $P_\text{hyd,crue} / P_\text{hyd,nominale}$ et commenter. (3 points)

---

## PHASE 3 — Conception préliminaire de la transmission *(25 points)*

### Question 3.1 — Choix de la transmission (8 points)

La génératrice synchrone à aimants permanents (GSAP) a une **vitesse nominale de 750 tr/min** pour une fréquence de réseau de 50 Hz et 4 paires de pôles.

**Q 3.1.a** — Calculer le rapport de multiplication $\mu$ nécessaire pour adapter la vitesse de la turbine ($n_\text{opt}$) à la vitesse de la génératrice (750 tr/min) :

$$\mu = \frac{n_\text{gen}}{n_\text{turbine}}$$

(2 points)

**Q 3.1.b** — Identifier les **deux solutions techniques** principales pour la transmission entre la turbine et la génératrice :
1. Transmission directe (sans multiplicateur)
2. Transmission avec multiplicateur épicycloïdal

Compléter le tableau comparatif :

| Critère | Transmission directe | Multiplicateur épicycloïdal |
|---|---|---|
| Rapport de vitesse | — | — |
| Rendement | ~1 (idéal) | 0,96 |
| Encombrement | Faible | Moyen |
| Complexité maintenance | Faible | Élevée |
| Coût | Faible | Élevé |
| Adapté à ce cas ? | À discuter | À discuter |

(4 points)

**Q 3.1.c** — Proposer et **justifier** le choix de transmission retenu pour l'HydroFlux-V5. (2 points)

---

### Question 3.2 — Dimensionnement de l'arbre de turbine (12 points)

L'arbre central de la turbine est un cylindre plein en **acier inoxydable 316L** :

| Propriété | Valeur |
|---|---|
| Module de cisaillement | $G = 77 \, \text{GPa}$ |
| Limite élastique | $R_e = 220 \, \text{MPa}$ |
| Résistance à la traction | $R_m = 540 \, \text{MPa}$ |
| Résistance à la corrosion | Excellente (milieu aquatique) |

L'arbre transmet le couple $C_\text{turbine}$ calculé en Q 2.3.a. Il est sollicité en **torsion pure**.

#### Données géométriques de l'arbre

- Longueur entre paliers : $l = 1{,}8 \, \text{m}$
- Diamètre à déterminer : $d$ (m)
- Section transversale : $S_\text{arbre} = \pi d^2 / 4$
- Moment polaire d'inertie : $I_p = \pi d^4 / 32$

**Q 3.2.a** — Rappeler la relation entre la contrainte de cisaillement maximale $\tau_\text{max}$, le couple $C$, le diamètre $d$ et le moment polaire $I_p$ :

$$\tau_\text{max} = \frac{C \cdot d/2}{I_p} = \frac{16 \cdot C}{\pi \cdot d^3}$$

(1 point)

**Q 3.2.b** — En appliquant le critère de résistance en torsion avec un coefficient de sécurité $s = 2$ :

$$\tau_\text{adm} = \frac{R_e}{s \cdot \sqrt{3}}$$

Calculer $\tau_\text{adm}$ pour l'acier 316L. (2 points)

**Q 3.2.c** — À partir de la condition $\tau_\text{max} \leq \tau_\text{adm}$, exprimer et calculer le **diamètre minimal** $d_\text{min}$ de l'arbre :

$$d_\text{min} = \left(\frac{16 \cdot C}{\pi \cdot \tau_\text{adm}}\right)^{1/3}$$

Utiliser $C = C_\text{max}$ (couple en crue, résultat de Q 2.3.b) pour le dimensionnement. (4 points)

**Q 3.2.d** — Choisir un diamètre normalisé $d$ parmi la série : 30 / 35 / 40 / 45 / 50 / 55 / 60 mm. Justifier le choix. (2 points)

**Q 3.2.e** — Vérifier la **rigidité en torsion** : l'angle de torsion $\phi$ doit être inférieur à 0,5° par mètre. La formule est :

$$\phi = \frac{C \cdot l}{G \cdot I_p} \quad \text{(en radians)}$$

Calculer $\phi$ pour $l = 1{,}0 \, \text{m}$ et vérifier le critère. (3 points)

---

### Question 3.3 — Choix des matériaux de l'arbre (5 points)

**Q 3.3.a** — Justifier le choix de l'**acier inoxydable 316L** pour l'arbre en milieu fluvial, en précisant :
- La composition chimique approximative (teneur en Cr, Ni, Mo)
- Le type de corrosion auquel il résiste
- Ses avantages et inconvénients par rapport à l'acier carbone 42CrMo4 (2 points)

**Q 3.3.b** — Proposer un traitement de surface complémentaire pour les zones de contact (paliers, joints) et justifier votre choix. (1 point)

**Q 3.3.c** — Un candidat propose de remplacer l'arbre en acier 316L par un arbre en **polymère composite fibres de verre/époxy** (GFRP). Évaluer la pertinence de cette proposition en comparant les modules de cisaillement ($G_\text{GFRP} = 7 \, \text{GPa}$ vs $G_{316L} = 77 \, \text{GPa}$) et les limites en cisaillement. Conclure. (2 points)

---

## PHASE 4 — Validation et bilan *(20 points)*

### Question 4.1 — Bilan énergétique de la chaîne (8 points)

**Q 4.1.a** — Compléter le bilan énergétique de la chaîne complète à la vitesse nominale $V_n = 2{,}5 \, \text{m/s}$ :

| Étape | Formule | Valeur numérique |
|---|---|---|
| Puissance hydraulique disponible | $P_\text{hyd} = \frac{1}{2} \rho S V_n^3$ | **[1]** kW |
| Puissance mécanique turbine | $P_\text{méca} = C_p \cdot P_\text{hyd}$ | **[2]** kW |
| Puissance après multiplicateur | $P_\text{multi} = \eta_\text{multi} \cdot P_\text{méca}$ | **[3]** kW |
| Puissance électrique (génératrice) | $P_\text{élec} = \eta_\text{gen} \cdot P_\text{multi}$ | **[4]** kW |
| Rendement global de la chaîne | $\eta_\text{global} = P_\text{élec} / P_\text{hyd}$ | **[5]** |

(5 points)

**Q 4.1.b** — Calculer le **rendement global** $\eta_\text{global}$ et le comparer à la limite de Betz. Commenter les pertes à chaque étage. (3 points)

---

### Question 4.2 — Production annuelle d'énergie (7 points)

On utilise la table de distribution des vitesses (DR-2, Phase 1) et le modèle simplifié suivant :

- Pour $V < V_\text{min} = 1{,}5 \, \text{m/s}$ : turbine à l'arrêt, $P_\text{élec} = 0$
- Pour $V_\text{min} \leq V < V_n$ : puissance électrique réduite selon $P_\text{élec}(V) = P_n \times (V/V_n)^3 \times \eta_\text{global}$ (simplification)
- Pour $V \geq V_n$ : puissance électrique limitée à $P_n = 5 \, \text{kW}$ (régulation)
- Pour $V > V_\text{survie} = 4{,}0 \, \text{m/s}$ : turbine en veille (protection crue)

**Q 4.2.a** — Pour chaque plage de vitesse de la table DR-2, calculer la **puissance électrique moyenne** $\bar{P}_\text{élec}$ (utiliser la vitesse médiane de chaque plage). Présenter les résultats dans un tableau. (4 points)

**Q 4.2.b** — Calculer la **production annuelle d'énergie** $E_\text{an}$ (en kWh/an) en sommant les contributions de chaque plage :

$$E_\text{an} = \sum_i \bar{P}_{\text{élec},i} \times \Delta t_i$$

(2 points)

**Q 4.2.c** — Comparer la production annuelle à la consommation annuelle d'un foyer français moyen (environ 4 500 kWh/an). Combien de foyers l'HydroFlux-V5 pourrait-elle alimenter ? (1 point)

---

### Question 4.3 — Comparaison avec le cahier des charges et propositions d'amélioration (5 points)

**Q 4.3.a** — Compléter le tableau de validation des exigences :

| Exigence (CdCF) | Valeur requise | Valeur calculée | Conforme ? |
|---|---|---|---|
| Puissance nominale $P_n$ | $\geq 5 \, \text{kW}$ | — | — |
| Durée de fonctionnement | $\geq 3\,200 \, \text{h/an}$ | — | — |
| Vitesse de rotation | $\leq 60 \, \text{tr/min}$ | — | — |
| Survie en crue | Oui ($V \leq 4 \, \text{m/s}$) | — | — |

(2 points)

**Q 4.3.b** — Proposer **trois améliorations techniques** permettant d'augmenter la production annuelle d'énergie de l'HydroFlux-V5, en justifiant l'impact de chaque proposition sur les paramètres $C_p$, $S$, $V$ ou $\eta$. (3 points)

---

*— Fin du sujet —*

*Rappel des résultats intermédiaires utiles si vous n'avez pas résolu les questions précédentes :*
- *Puissance hydraulique nominale : $P_\text{hyd} \approx 23{,}4 \, \text{kW}$*
- *Couple turbine nominal : $C_\text{turbine} \approx 893 \, \text{N·m}$*
- *Couple turbine en crue : $C_\text{max} \approx 3\,840 \, \text{N·m}$*
- *Vitesse angulaire optimale : $\omega_\text{opt} \approx 6{,}25 \, \text{rad/s}$*
