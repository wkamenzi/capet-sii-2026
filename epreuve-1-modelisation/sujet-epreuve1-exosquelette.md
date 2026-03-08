# CAPET SII — Ingénierie Mécanique — Session 2026
## Épreuve 1 : Modélisation d'un produit
### Durée : 4 heures — Coefficient 3 — Note sur 20

---

> **Document d'entraînement non officiel — Usage pédagogique exclusivement**

---

## Instructions générales

- Les parties **A, B et F sont obligatoires** (60 points sur 100 au barème brut).
- Le candidat choisit **deux parties parmi C, D et E** (40 points).
- La note finale est ramenée sur 20.
- Les différentes parties sont **indépendantes** ; il est conseillé de ne pas bloquer sur une question.
- Le soin apporté à la rédaction et à la présentation des calculs sera valorisé.
- Une **calculatrice non programmable** est autorisée.
- Sauf indication contraire, on prendra $g = 9{,}81 \, \text{m/s}^2$.

---

## Présentation du système — Exosquelette d'assistance industrielle EXOARM-S3

### Contexte

Les troubles musculo-squelettiques (TMS) représentent la première cause de maladies professionnelles en France, avec plus de **40 000 cas reconnus par an** et un coût annuel estimé à **2 milliards d'euros** pour les entreprises (source : INRS, 2023). Les secteurs les plus touchés sont l'automobile, l'aéronautique et la logistique, où les opérateurs effectuent des tâches répétitives bras levés : vissage en plafond, câblage en hauteur, peinture de carrosserie.

Pour répondre à cette problématique, la société fictive **MécanAssist** a développé l'**EXOARM-S3**, un exosquelette passif d'assistance aux membres supérieurs destiné aux environnements industriels. Il est porté comme un sac à dos et transfère une partie de l'effort de soutien des bras vers le tronc de l'opérateur, réduisant ainsi la fatigue musculaire à l'épaule.

### Description technique

L'EXOARM-S3 est un exosquelette **passif** (sans motorisation) fonctionnant par **ressorts à gaz** précontraints. Il assiste les deux membres supérieurs indépendamment pour les tâches en élévation (angle d'épaule entre 45° et 150°).

**Figure 1 — Vue générale de l'EXOARM-S3** *(voir fichier schemas-descriptions.md)*

#### Données constructeur

| Paramètre | Valeur |
|---|---|
| Masse totale de l'exosquelette | $m_\text{exo} = 3{,}5 \, \text{kg}$ |
| Taille des opérateurs compatibles | 1,60 m à 1,95 m |
| Amplitude d'assistance en flexion d'épaule | $0°$ à $150°$ |
| Réduction de l'effort musculaire à l'épaule | 30 % à 50 % (selon la charge portée) |
| Nombre de degrés de liberté actifs | 2 (flexion/extension de chaque épaule) |
| Matériaux principaux | Aluminium 7075-T6, composite carbone/époxy, polyamide PA66 |
| Certification | EN ISO 13482 (robots de service — sécurité) |
| Durée de vie des ressorts à gaz | 2 millions de cycles |

#### Caractéristiques des matériaux

| Matériau | Module de Young $E$ (GPa) | Limite élastique $R_e$ (MPa) | Masse volumique $\rho$ (kg/m³) |
|---|---|---|---|
| Aluminium 7075-T6 | 71 | 503 | 2 810 |
| Composite carbone/époxy (UD) | 135 | 1 200 | 1 550 |
| Acier 42CrMo4 (axes) | 210 | 650 | 7 850 |
| Polyamide PA66 (glissières) | 3 | 80 | 1 140 |

#### Architecture mécanique simplifiée (côté droit)

La chaîne cinématique du côté droit comprend les solides suivants :
- **S0** : Châssis dorsal (lié à l'opérateur, considéré fixe dans cette étude)
- **S1** : Attelle d'épaule (liaison pivot d'axe horizontal $\Delta_1$ avec S0, angle $\theta_1$)
- **S2** : Bras articulé supérieur (liaison pivot d'axe $\Delta_2$ parallèle à $\Delta_1$ avec S1, angle $\theta_2$)
- **S3** : Manchon bras (liaison encastrement avec S2, en contact avec l'avant-bras de l'opérateur)
- **R1** : Ressort à gaz (relie S0 à S2 par deux pivots)

**Données géométriques** :
- Longueur de l'attelle d'épaule S1 : $L_1 = 0{,}18 \, \text{m}$
- Longueur du bras articulé S2 : $L_2 = 0{,}32 \, \text{m}$
- Distance entre $\Delta_1$ et le point d'accroche inférieur du ressort sur S0 : $d_0 = 0{,}12 \, \text{m}$
- Distance entre $\Delta_2$ et le point d'accroche supérieur du ressort sur S2 : $d_2 = 0{,}10 \, \text{m}$
- Masse du bras articulé S2 : $m_2 = 0{,}45 \, \text{kg}$, centre de gravité au milieu de S2
- Masse de l'outil tenu par l'opérateur : $m_\text{outil} = 2{,}0 \, \text{kg}$
- Masse du bras de l'opérateur (segment bras + avant-bras) : $m_\text{bras} = 4{,}0 \, \text{kg}$, centre de gravité à $l_G = 0{,}30 \, \text{m}$ de l'axe $\Delta_1$

**Caractéristique du ressort à gaz R1** :
- Force à l'extension nominale : $F_0 = 180 \, \text{N}$
- Variation de force sur la course : $\pm 15 \, \text{N}$ (ressort quasi-isobare)
- Course totale : $120 \, \text{mm}$

---

## PARTIE A — Analyse fonctionnelle et cahier des charges *(Obligatoire — 20 points)*

### Question A1 — Diagramme pieuvre (6 points)

Le diagramme pieuvre (ou diagramme des interactions) permet d'identifier les fonctions de service d'un produit en relation avec son environnement.

**On identifie les éléments du milieu extérieur suivants :**
- Opérateur
- Outil industriel
- Environnement de travail (espace, obstacles)
- Norme de sécurité EN ISO 13482
- Réseau de maintenance
- Énergie (potentielle des ressorts)

**Q A1.a** — En vous appuyant sur la description du système, identifier la **fonction principale (FP)** de l'EXOARM-S3 et rédiger son intitulé sous la forme : *"Permettre à … de … en …"* (2 points)

**Q A1.b** — Identifier **quatre fonctions contraintes (FC)** en justifiant brièvement chacune. Vous les numéroterez FC1 à FC4. (4 points)

---

### Question A2 — Diagramme des exigences SysML (8 points)

Le tableau ci-dessous présente un extrait du cahier des charges fonctionnel de l'EXOARM-S3. Certains éléments sont volontairement incomplets (cases vides ou valeurs manquantes).

| ID | Exigence | Critère | Niveau | Flexibilité |
|---|---|---|---|---|
| EX-01 | Assister la flexion d'épaule | Réduction effort musculaire | **[1]** | ± 5 % |
| EX-02 | S'adapter à la morphologie | Taille opérateur | 1,60 m à 1,95 m | **[2]** |
| EX-03 | Ne pas gêner les mouvements libres | Amplitude sans résistance en dehors de 0°-150° | 0 N de résistance | Non négociable |
| EX-04 | **[3]** | Masse de l'exosquelette | < 4 kg | Négociable ± 0,5 kg |
| EX-05 | Résister aux chocs et à l'usure | Durée de vie des ressorts | **[4]** | ± 10 % |
| EX-06 | Assurer la sécurité de l'opérateur | Conformité norme EN ISO 13482 | Obligatoire | Non négociable |

**Q A2.a** — Compléter les cases **[1]**, **[2]**, **[3]** et **[4]** en justifiant vos choix. (4 points)

**Q A2.b** — Parmi les exigences listées, distinguer celles relevant de la **fonction principale** et celles relevant des **fonctions contraintes**. (2 points)

**Q A2.c** — Proposer une exigence supplémentaire non listée dans le tableau, en précisant son critère et son niveau. (2 points)

---

### Question A3 — Chaîne d'énergie et chaîne d'information (6 points)

L'EXOARM-S3 est un système passif. Son fonctionnement peut néanmoins être décrit par une chaîne d'énergie et, pour une version active future, par une chaîne d'information.

**Q A3.a** — Compléter le schéma de chaîne d'énergie ci-dessous en nommant les blocs fonctionnels :

```
[Énergie stockée   ] → [   [A]   ] → [   [B]   ] → [   [C]   ] → [Effet utile :
 dans les ressorts ]    (transmettre) (adapter)     (convertir)    réduction effort]
```

Nommer les blocs **[A]**, **[B]**, **[C]** en les associant aux éléments physiques de l'EXOARM-S3. (3 points)

**Q A3.b** — Dans une version active motorisée de l'exosquelette, le moteur brushless est piloté par un capteur EMG (électromyographie) mesurant l'activité musculaire. Proposer un schéma de la chaîne d'information en identifiant : le capteur, le traitement du signal, l'actionneur et la boucle de retour. (3 points)

---

## PARTIE B — Modélisation cinématique *(Obligatoire — 25 points)*

### Question B4 — Schéma cinématique (6 points)

**Q B4** — Réaliser le **schéma cinématique** de la chaîne articulée du côté droit de l'EXOARM-S3 (solides S0, S1, S2, S3 et ressort R1). Pour chaque liaison, préciser :
- La nature de la liaison (pivot, encastrement, pivot-glissant, etc.)
- L'axe de la liaison
- Le solide porteur et le solide porté

Représenter le schéma dans le plan sagittal (plan de la flexion d'épaule). Utiliser les conventions suivantes :
- Liaison pivot : cercle avec axe
- Liaison encastrement : hachurage
- Ressort : symbole zigzag

---

### Question B5 — Mobilité (formule de Grübler) (5 points)

On modélise la chaîne cinématique du côté droit comme suit :
- **4 classes d'équivalence** (S0 à S3, sans compter R1 qui introduit une liaison supplémentaire)
- **Liaisons** : 3 pivots d'axe $z$ (entre S0/S1, S1/S2, S2/S3) + 1 liaison sphérique en A (accroche basse du ressort sur S0) + 1 liaison sphérique en B (accroche haute du ressort sur S2)

La formule de Grübler dans le plan (2D) est :

$$M = 3(n - 1) - \sum_{i} (6 - m_i)$$

où $n$ est le nombre de classes d'équivalence (pièces + bâti), $m_i$ est le nombre de degrés de mobilité de la liaison $i$.

En 2D, on utilise :

$$M = 3(n - 1) - \sum_{i} c_i$$

où $c_i$ est le nombre de contraintes de la liaison $i$ (pour un pivot plan : $c_i = 2$).

**Q B5.a** — Recenser toutes les liaisons du mécanisme, en précisant pour chacune le nombre de degrés de liberté (ddl) et le nombre de contraintes $c_i$ dans le plan. (2 points)

**Q B5.b** — Appliquer la formule de Grübler et calculer le degré de mobilité $M$. Interpréter le résultat. (3 points)

---

### Question B6 — Loi entrée-sortie (8 points)

On se place dans le plan sagittal. On note :
- $\theta_1$ : angle de flexion de S1 par rapport à S0 (angle d'épaule, mesuré depuis la verticale)
- $\theta_2$ : angle de S2 par rapport à S1 (angle relatif)
- $\theta_\text{eff}$ : angle de l'effecteur (manchon S3) par rapport à la verticale

On souhaite exprimer $\theta_\text{eff}$ en fonction de $\theta_1$ uniquement, sachant que par conception, la liaison entre S1 et S2 est une **liaison pivot d'axe fixe avec blocage géométrique** qui impose $\theta_2 = k \cdot \theta_1$ avec $k = 0{,}5$ (rapport de transmission par câble et poulie interne).

**Q B6.a** — Exprimer la relation entre $\theta_\text{eff}$, $\theta_1$ et $\theta_2$. (2 points)

**Q B6.b** — En déduire la loi entrée-sortie $\theta_\text{eff} = f(\theta_1)$. (2 points)

**Q B6.c** — Calculer numériquement $\theta_\text{eff}$ pour $\theta_1 = 0°$, $\theta_1 = 60°$, $\theta_1 = 90°$, $\theta_1 = 120°$ et $\theta_1 = 150°$. Présenter les résultats dans un tableau. (2 points)

**Q B6.d** — Tracer l'allure de $\theta_\text{eff}$ en fonction de $\theta_1$ sur l'intervalle $[0°; 150°]$. Caractériser la nature de cette loi. (2 points)

---

### Question B7 — Vérification de l'amplitude articulaire (6 points)

**Q B7.a** — D'après le cahier des charges, quelle est l'amplitude maximale de flexion d'épaule requise ? Retrouver cette valeur dans le tableau des exigences. (1 point)

**Q B7.b** — La course du ressort à gaz R1 est de $c = 120 \, \text{mm}$. Le ressort est en configuration tendue pour $\theta_1 = 0°$ (longueur $L_\text{max} = 280 \, \text{mm}$) et comprimée pour $\theta_1 = 150°$ (longueur $L_\text{min} = 160 \, \text{mm}$). Vérifier géométriquement que cette course est compatible avec le débattement angulaire requis. On utilisera la relation des cosinus dans le triangle formé par les deux points d'accroche du ressort et l'axe $\Delta_2$ :

$$L(\theta_1) = \sqrt{d_0^2 + d_2^2 - 2 d_0 d_2 \cos(\theta_1 + \phi_0)}$$

avec $\phi_0 = 30°$ (angle géométrique de montage), $d_0 = 0{,}12 \, \text{m}$, $d_2 = 0{,}10 \, \text{m}$.

Calculer $L(0°)$ et $L(150°)$ et en déduire la course effective. Conclure. (5 points)

---

## PARTIE C — Dimensionnement statique *(Au choix — 20 points)*

### Question C8 — Isolement et bilan des actions (6 points)

On isole le système $\{S2 + \text{bras opérateur} + \text{outil}\}$ considéré en équilibre statique à $\theta_1 = 90°$ (bras horizontal).

**Données** :
- Masse du bras articulé S2 : $m_2 = 0{,}45 \, \text{kg}$, centre de gravité $G_2$ à $L_2/2 = 0{,}16 \, \text{m}$ de $\Delta_1$
- Masse du bras opérateur : $m_\text{bras} = 4{,}0 \, \text{kg}$, centre de gravité à $l_G = 0{,}30 \, \text{m}$ de $\Delta_1$
- Masse de l'outil : $m_\text{outil} = 2{,}0 \, \text{kg}$, appliqué à $l_\text{outil} = 0{,}60 \, \text{m}$ de $\Delta_1$
- Force du ressort R1 : $\vec{F}_{R1}$, dirigée selon l'axe du ressort, dont l'angle avec l'horizontale est $\alpha = 40°$ à $\theta_1 = 90°$

**Q C8.a** — Réaliser le bilan des actions mécaniques extérieures s'appliquant sur le système isolé (schéma PFS avec vecteurs forces). Identifier chaque action (poids, liaison, ressort). (3 points)

**Q C8.b** — Écrire les équations d'équilibre en translation ($\sum \vec{F} = \vec{0}$) et en rotation par rapport à $\Delta_1$ ($\sum M_{\Delta_1} = 0$). (3 points)

---

### Question C9 — Calcul de l'effort du ressort (7 points)

**Q C9.a** — D'après l'équation de moment en $\Delta_1$ (question C8), exprimer la force $F_{R1}$ du ressort nécessaire pour maintenir l'équilibre. (3 points)

**Q C9.b** — Calculer numériquement $F_{R1}$. Vérifier que la valeur trouvée est cohérente avec la force nominale du ressort à gaz ($F_0 = 180 \, \text{N}$). (2 points)

**Q C9.c** — L'exosquelette doit compenser 40 % de l'effort musculaire total. L'effort musculaire $M_\text{musc}$ (couple à l'épaule) sans exosquelette vaut :

$$M_\text{musc,sans} = (m_\text{bras} \cdot l_G + m_\text{outil} \cdot l_\text{outil}) \cdot g \cdot \sin(\theta_1)$$

Calculer $M_\text{musc,sans}$ pour $\theta_1 = 90°$. En déduire le couple d'assistance $M_\text{assist}$ fourni par le ressort, et vérifier qu'il représente bien 40 % de $M_\text{musc,sans}$. (2 points)

---

### Question C10 — Vérification de la contrainte dans l'axe d'articulation (7 points)

L'axe de la liaison pivot $\Delta_1$ (entre S0 et S1) est un cylindre creux en acier 42CrMo4 de :
- Diamètre extérieur : $d_e = 16 \, \text{mm}$
- Diamètre intérieur : $d_i = 10 \, \text{mm}$
- Section transversale : $S_\text{axe}$
- Longueur entre appuis : $l_\text{axe} = 40 \, \text{mm}$

L'axe est sollicité en **cisaillement pur** par la force de réaction $R_{\Delta_1}$ exercée par S1 sur S0.

**Q C10.a** — Calculer la section transversale $S_\text{axe}$ de l'axe creux. (1 point)

**Q C10.b** — À partir des équations d'équilibre (question C8b), calculer les composantes $R_x$ et $R_y$ de la réaction en $\Delta_1$, puis la norme $R_{\Delta_1} = \sqrt{R_x^2 + R_y^2}$. (3 points)

**Q C10.c** — Calculer la contrainte de cisaillement $\tau = R_{\Delta_1} / S_\text{axe}$. Vérifier le critère de Von Mises : $\sigma_\text{eq} = \sqrt{3} \cdot \tau \leq R_e / s$ avec $s = 2$ (coefficient de sécurité) et $R_e = 650 \, \text{MPa}$. Conclure sur la résistance de l'axe. (3 points)

---

## PARTIE D — Résistance des matériaux *(Au choix — 20 points)*

### Question D11 — Modélisation de la barre de support (4 points)

La barre de support dorsale de l'EXOARM-S3 est un profilé tubulaire rectangulaire en aluminium 7075-T6. Elle relie le harnais dorsal (encastrement en A) au mécanisme articulaire d'épaule. On la modélise comme une **poutre encastrée-libre** :

- Longueur : $L = 0{,}40 \, \text{m}$
- Section rectangulaire creuse : $b \times h = 30 \times 20 \, \text{mm}$, épaisseur $e = 2 \, \text{mm}$
- Module de Young : $E = 71 \, \text{GPa}$
- Force appliquée en bout libre B : $F = 85 \, \text{N}$ (verticalement, vers le bas, représentant la réaction au niveau de l'épaule)

**Q D11.a** — Schématiser la poutre avec ses conditions aux limites et les sollicitations. Identifier le type de chargement. (2 points)

**Q D11.b** — Calculer le moment d'inertie $I_z$ de la section creuse par rapport à l'axe neutre $z$ (axe horizontal passant par le centre de gravité) :

$$I_z = \frac{b \cdot h^3 - (b-2e)(h-2e)^3}{12}$$

Application numérique avec $b = 30 \, \text{mm}$, $h = 20 \, \text{mm}$, $e = 2 \, \text{mm}$. (2 points)

---

### Question D12 — Diagrammes des efforts intérieurs (6 points)

On repère l'abscisse $x$ depuis l'encastrement A ($x = 0$) vers l'extrémité libre B ($x = L$).

**Q D12.a** — Par la méthode des coupes, exprimer en fonction de $x$ :
- Le torseur de cohésion $\{T_c(x)\}$ : effort tranchant $T(x)$ et moment fléchissant $M_f(x)$ dans une section courante à l'abscisse $x$.
(3 points)

**Q D12.b** — Tracer soigneusement les diagrammes $T(x)$ et $M_f(x)$ sur l'intervalle $[0; L]$, en précisant les valeurs aux extrémités et en indiquant les signes. (3 points)

---

### Question D13 — Flèche maximale et critère de rigidité (5 points)

La flèche d'une poutre encastrée-libre chargée en bout vaut :

$$f_\text{max} = \frac{F \cdot L^3}{3 \cdot E \cdot I_z}$$

**Q D13.a** — Calculer numériquement la flèche maximale $f_\text{max}$. (2 points)

**Q D13.b** — Le cahier des charges impose un critère de rigidité : $f_\text{max} \leq L/200$. Calculer $L/200$ et conclure sur le respect du critère. (2 points)

**Q D13.c** — Si le critère n'est pas respecté, proposer une modification de section (sans changer la masse) permettant d'y satisfaire. (1 point)

---

### Question D14 — Comparaison de matériaux (5 points)

On envisage de remplacer l'aluminium 7075-T6 par un composite carbone/époxy unidirectionnel (UD) pour la barre de support.

| Matériau | $E$ (GPa) | $\rho$ (kg/m³) | $R_e$ (MPa) |
|---|---|---|---|
| Aluminium 7075-T6 | 71 | 2 810 | 503 |
| Composite C/époxy UD | 135 | 1 550 | 1 200 |

**Q D14.a** — Pour une rigidité identique ($E \cdot I_z = \text{const}$), calculer le rapport des moments d'inertie $I_{z,C} / I_{z,Al}$ nécessaire. En déduire le rapport des hauteurs de section $h_C / h_{Al}$ (à largeur constante). (3 points)

**Q D14.b** — Calculer le rapport des masses volumiques et estimer le gain de masse en passant à la solution composite (en supposant que la géométrie de la section composite est celle déduite en Q D14.a). (2 points)

---

## PARTIE E — Modélisation dynamique *(Au choix — 20 points)*

### Question E15 — Modèle dynamique simplifié (6 points)

On modélise le mouvement de levée du bras (membre supérieur + outil + S2) comme la rotation d'un **solide équivalent** autour de l'axe $\Delta_1$, avec :
- Moment d'inertie total autour de $\Delta_1$ : $J = 0{,}75 \, \text{kg·m}^2$
- Couple résistant gravitaire (poids des éléments) : $C_\text{grav}(\theta_1) = (m_\text{bras} \cdot l_G + m_\text{outil} \cdot l_\text{outil}) \cdot g \cdot \cos(\theta_1)$ — *Attention : le signe dépend de la convention angulaire.*
- Couple assisté par le ressort : $C_\text{ressort}(\theta_1) = F_{R1}(\theta_1) \cdot d_2 \cdot \sin(\alpha(\theta_1))$

Pour simplifier, on suppose que le ressort fournit un couple d'assistance **constant** $C_\text{ressort} = 25 \, \text{N·m}$ sur toute la course.

**Q E15.a** — Écrire le Principe Fondamental de la Dynamique (PFD) en rotation autour de $\Delta_1$ pour le levée du bras de $\theta_1 = 0°$ à $\theta_1 = 90°$ :

$$J \cdot \ddot{\theta}_1 = \sum C_{\Delta_1}$$

Identifier tous les couples intervenants (poids, ressort, muscles). (3 points)

**Q E15.b** — En faisant l'hypothèse que le couple musculaire est **nul** (cas de test — l'exosquelette compense tout), simplifier l'équation du mouvement. (3 points)

---

### Question E16 — Couple résistant en fonction de la vitesse angulaire (6 points)

On introduit un amortissement visqueux (joint élastomère de l'articulation) de coefficient $b = 0{,}8 \, \text{N·m·s/rad}$.

L'équation du mouvement devient :

$$J \cdot \ddot{\theta}_1 + b \cdot \dot{\theta}_1 = C_\text{ressort} - C_\text{grav}(\theta_1)$$

**Q E16.a** — À $\theta_1 = 45°$ et $\dot{\theta}_1 = 1{,}5 \, \text{rad/s}$, calculer numériquement :
- $C_\text{grav}(45°)$
- Le terme d'amortissement $b \cdot \dot{\theta}_1$
- L'accélération angulaire $\ddot{\theta}_1$ (3 points)

**Q E16.b** — Calculer la **vitesse angulaire limite** $\dot{\theta}_{1,\text{lim}}$ pour laquelle l'accélération $\ddot{\theta}_1$ s'annule à $\theta_1 = 45°$. Interpréter physiquement ce résultat. (3 points)

---

### Question E17 — Temps de réponse du système (8 points)

On veut simuler le mouvement de levée de bras de $0°$ à $90°$ en $t_f = 0{,}8 \, \text{s}$.

**Q E17.a** — On suppose un mouvement à **accélération angulaire constante** $\ddot{\theta}_1 = \text{const}$. Exprimer $\ddot{\theta}_1$ en fonction de $\theta_\text{final}$ et $t_f$. Calculer numériquement $\ddot{\theta}_1$. (2 points)

**Q E17.b** — En déduire le couple total nécessaire $C_\text{total} = J \cdot \ddot{\theta}_1$ pour réaliser ce mouvement. (1 point)

**Q E17.c** — À mi-course ($\theta_1 = 45°$, $t = 0{,}4 \, \text{s}$), calculer la vitesse angulaire $\dot{\theta}_1 = \ddot{\theta}_1 \cdot t$ et vérifier que le terme d'amortissement reste négligeable (< 10 % du couple total). (2 points)

**Q E17.d** — Calculer la puissance mécanique moyenne $P_\text{moy}$ développée lors du mouvement :

$$P_\text{moy} = C_\text{total} \cdot \dot{\theta}_{1,\text{moy}}$$

avec $\dot{\theta}_{1,\text{moy}} = \theta_\text{final} / t_f$ (approximation trapèze). (2 points)

**Q E17.e** — Commenter le résultat en le comparant à la puissance maximale d'un opérateur humain au niveau de l'épaule (valeur de référence ergonomique : $P_\text{max} \approx 50 \, \text{W}$ en travail répétitif). (1 point)

---

## PARTIE F — Synthèse *(Obligatoire — 15 points)*

### Question F18 — Bilan des performances modélisées (5 points)

**Q F18** — Remplir le tableau de synthèse ci-dessous en utilisant les résultats obtenus dans les parties précédentes (ou des estimations raisonnables si vous n'avez pas traité toutes les parties) :

| Exigence (cahier des charges) | Valeur visée | Valeur modélisée | Écart | Conforme ? |
|---|---|---|---|---|
| Réduction de l'effort musculaire | 40 % | — | — | — |
| Amplitude en flexion d'épaule | 0° à 150° | — | — | — |
| Flèche de la barre support ($f \leq L/200$) | $\leq 2 \, \text{mm}$ | — | — | — |
| Contrainte dans l'axe ($\sigma_\text{eq} \leq R_e/s$) | $\leq 325 \, \text{MPa}$ | — | — | — |
| Temps de levée bras 0°→90° | $\leq 0{,}8 \, \text{s}$ | — | — | — |

Conclure globalement sur la validité du concept EXOARM-S3. (5 points)

---

### Question F19 — Propositions d'améliorations de conception (5 points)

**Q F19.a** — Identifier **deux limites** du modèle statique utilisé en Partie C (hypothèses simplificatrices). (2 points)

**Q F19.b** — Proposer **deux améliorations techniques** concrètes de l'EXOARM-S3 (mécanique, matériaux, commande), en justifiant leur intérêt. (3 points)

---

### Question F20 — Impact sociétal et environnemental (5 points)

**Q F20.a** — Identifier les parties prenantes de l'EXOARM-S3 et leurs intérêts respectifs (opérateur, entreprise, société, environnement). (2 points)

**Q F20.b** — Analyser l'impact environnemental de l'exosquelette sur l'ensemble de son cycle de vie (fabrication, utilisation, fin de vie). Vous mobiliserez le concept d'**ACV** (Analyse du Cycle de Vie). (2 points)

**Q F20.c** — À votre avis, l'utilisation d'exosquelettes en industrie remplace-t-elle le travail humain ou améliore-t-elle ses conditions ? Argumenter en 5 à 10 lignes. (1 point)

---

*— Fin du sujet —*

*Le candidat vérifiera qu'il a bien traité les parties A, B et F (obligatoires) et exactement deux parties parmi C, D et E (au choix).*
