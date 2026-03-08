# Sujets d'entraînement — CAPET SII Ingénierie Mécanique 2026

> ⚠️ **Avertissement** : Ces sujets sont des **documents d'entraînement non officiels**, créés à des fins pédagogiques. Ils ne sont en aucun cas des sujets officiels du ministère de l'Éducation nationale. Toute ressemblance avec les sujets officiels de la session 2026 serait purement fortuite.

---

## Présentation de la nouvelle maquette 2026

Le CAPET SII (Certificat d'Aptitude au Professorat de l'Enseignement Technique — Sciences Industrielles de l'Ingénieur), option **Ingénierie Mécanique**, a été rénové à compter de la session 2026. Les épreuves d'admissibilité sont désormais au nombre de deux :

### Épreuve 1 — Modélisation d'un produit
- **Durée** : 4 heures
- **Coefficient** : 3
- **Notée sur** : 20 points
- **Objectif** : Étude de la modélisation d'un produit pour en caractériser les performances, mobilisant les connaissances scientifiques et technologiques de l'option mécanique
- **Structure** : Plusieurs parties indépendantes ; certaines obligatoires, d'autres au choix du candidat

### Épreuve 2 — Résolution de problème
- **Durée** : 4 heures
- **Coefficient** : 2
- **Notée sur** : 20 points
- **Objectif** : Exploitation de ressources et de documents techniques, résolution d'un problème technique posé, établissement d'éléments de conception préliminaire

---

## Table des matières

### Épreuve 1 — Modélisation d'un produit
| Fichier | Description |
|---|---|
| [sujet-epreuve1-exosquelette.md](epreuve-1-modelisation/sujet-epreuve1-exosquelette.md) | Sujet complet — Exosquelette d'assistance industrielle |
| [corrige-epreuve1-exosquelette.md](epreuve-1-modelisation/corrige-epreuve1-exosquelette.md) | Corrigé détaillé avec calculs |
| [schemas-descriptions.md](epreuve-1-modelisation/schemas-descriptions.md) | Descriptions et schémas ASCII des figures |

### Épreuve 2 — Résolution de problème
| Fichier | Description |
|---|---|
| [sujet-epreuve2-hydrolienne.md](epreuve-2-resolution-probleme/sujet-epreuve2-hydrolienne.md) | Sujet complet — Hydrolienne fluviale à axe vertical |
| [corrige-epreuve2-hydrolienne.md](epreuve-2-resolution-probleme/corrige-epreuve2-hydrolienne.md) | Corrigé détaillé avec calculs |
| [schemas-descriptions.md](epreuve-2-resolution-probleme/schemas-descriptions.md) | Descriptions et schémas ASCII des figures |

---

## Thèmes des sujets

| Épreuve | Thème | Domaine |
|---|---|---|
| Épreuve 1 | Exosquelette d'assistance industrielle (type Comau MATE-XT / Exhauss) | Mécatronique, biomécanique, RDM |
| Épreuve 2 | Hydrolienne fluviale à axe vertical (type Darrieus) | Énergie, fluides, transmission |

---

## Instructions pour convertir les fichiers Markdown en Word (.docx)

### Méthode 1 — Pandoc (recommandée)

[Pandoc](https://pandoc.org/) est un convertisseur de documents universel. Installez-le depuis [pandoc.org/installing](https://pandoc.org/installing.html), puis exécutez :

```bash
# Conversion d'un seul fichier
pandoc sujet-epreuve1-exosquelette.md -o sujet-epreuve1-exosquelette.docx

# Avec rendu des formules mathématiques (nécessite une installation LaTeX)
pandoc sujet-epreuve1-exosquelette.md --mathml -o sujet-epreuve1-exosquelette.docx

# Avec un modèle Word personnalisé
pandoc sujet-epreuve1-exosquelette.md --reference-doc=modele.docx -o sujet-epreuve1-exosquelette.docx
```

### Méthode 2 — Copier-coller dans Word

1. Ouvrez le fichier `.md` dans un éditeur de texte (VS Code, Notepad++, etc.)
2. Copiez l'intégralité du contenu
3. Collez dans Microsoft Word
4. Reformatez manuellement les titres, tableaux et formules

### Méthode 3 — Éditeur Markdown en ligne

Utilisez [Dillinger.io](https://dillinger.io/) ou [StackEdit](https://stackedit.io/) :
1. Collez le contenu Markdown
2. Exportez en HTML, puis ouvrez dans Word (Fichier > Ouvrir l'URL ou copier le HTML)

### Note sur les formules mathématiques

Les formules sont écrites en **LaTeX** entre `$...$` (inline) ou `$$...$$` (bloc). Elles s'affichent correctement dans :
- GitHub (rendu natif)
- VS Code avec l'extension *Markdown Math*
- Typora
- Pandoc avec l'option `--mathjax` ou `--mathml`

---

## Prérequis pour les candidats

- Niveau scientifique visé : **Bac+3 à Bac+5** en ingénierie mécanique
- Connaissances mobilisées : mécanique des solides, RDM, analyse fonctionnelle (SysML), mécatronique, matériaux
- Outils autorisés à l'examen : calculatrice non programmable, documents fournis avec le sujet

---

*Dépôt maintenu par la communauté — Contributions bienvenues via Pull Request.*
