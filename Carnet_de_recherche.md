
## Carnet de recherche scientifique avec Python

<small>PyConFR 2019, Bordeaux</small>
<small>@c24b</small>
<small> DRISS</small>

---

### Qui parle ?

* c24b <small>(elle)</small>
* Python ~ [8-10] ans <small>(a perdu le compte)</small>
* Ex-ingé/corsaire de recherche <small>(INRA, Mines, CNRS,BnF, PSE)</small>

* Cheffe d'entreprise <small>(DRISS)</small>

---

DRISS (Digital Research In Science & Society)

Aider les chercheurs à :
<div class="fragment"> utiliser des outils open source</div>
<div class="fragment"> faciliter leur processus</div>
<div class="fragment"> faire de la recherche ouverte et reproductible</div>

---

## Carnet de recherche

### Pourquoi ?

---

![](software-research.png)

<small>Credits: @ixek</small>

---

### Le cycle modélisé

![](stack.png)

---

**Du coté des ingénieurs**

> Outiller et documenter le travail autour des données

*  <div class="fragment">médiation, redevabilité et transparence</div>

*  <div class="fragment">projet maintenable, reproductible, réutilisable</div>

---

**Du coté des chercheurs**

> Communiquer ses recherches et ses résultats

---

![](publish.png)

---

Plusieurs enjeux derrière la publication

* Collaboration 
* Expérimentation
* Evaluation par les pairs
* Publication (formats, contraintes, contenus)

---

Plusieurs enjeux derrière le développement

* Valider ses traitements
* Résultats réplicables
* Méthodes réutilisables

---

### Le cycle de recherche (modélisé)

![](stack.png)

---


![](stacktools.png)

---

> Gérer un projet de recherche comme du développement logiciel ?


- Tickets: hypothèses et plan d'analyse 
- Branches: analyse
- Releases: resultats + rédaction de l'article à publier

---

![](gitlab_workflow.png)

---

## Collaborer entre chercheurs

- s'accorder sur un langage descriptif simple et minimal commun
- travailler à plusieurs chercheurs 
- correction et reprise, historique et attribution  

---

## Outils pour la rédaction collaborative

|           |                  |                   |
|-----------|------------------|-------------------|
|markdown   |![](markdown.png) | [scholarly markdown](https://github.com/scholmd/scholmd/wiki)|
|git        |![](git.png)      | [git for research](https://github.com/dmgerman/git-for-research)     |
| gitlab    |![](gitlab-ce.png)| [gitlab for researcher](https://github.blog/2014-05-14-improving-github-for-science/) 

---

Ecrire en markdown des articles scientifiques:

- séparer le contenu de la présentation
- adapter le contenu à chaque format de présentation:
    - une présentation md2reveal
    - un article de blog md2html
    - un appel à proposition
    - un article de revue md2pdf
- gérer ses versions successives

---

Pour les débutants git 

GitLab-CE offre une interface web d'édition en ligne de markdown
![](gitlab-ce_webedit.png)


---

### Experimenter

Travail entre l'ingénieur et le chercheur

---

Pour le dev, plusieurs préoccupations:

* ne pas se rajouter du boulot
* code compréhensible, modifiable, appropriable
* environnement réplicable deployable et testable en ligne

---

Pour le chercheur:

* documentation claire et compréhensible
* test et expérimentation clé en main
* graphiques
* ajout de citation et de style

---

Le carnet de recherche

* dans un environnement replicable
* versionné et historicisé
* partageable modifiable et exportable

---

#### Créer un kernel spécifique pour jupyterlab:

A partir du fichier requirements.txt dans le projet

```bash
$ virtualenv ~/.sci-env --p /usr/bin/python3
$ source ~/.sci-env/bin/activate
(sci-env)$ pip install -r requirements.txt
```

---

# Un environnement os-indépendant


![https://hpc.guix.info/blog/2019/10/towards-reproducible-jupyter-notebooks/](guix.png)

---

### Documenter son code

Choix d'utiliser `py2nb`

```pip install py2nb```

* Versionnable en l'état
* Documentation intégrée

---


```python
#| # Testing ipython notebook
#| This is designed to demonstrate a simple script that converts a script into
#| a jupyter notebook with a simple additional markdown format.
#|
#| Code by default will be put into code cells
#|
#| * To make a markdown cell, prefix the comment line with with '#|'
#| * To split a code cell, add a line beginning with '#-'

import numpy
import matplotlib.pyplot as plt
%matplotlib inline

#| Here is a markdown cell.
#| Maths is also possible: $A=B$
#|
#| There are code cells below, split by '#-':

x = numpy.random.rand(5)

#-------------------------------

y = numpy.random.rand(4)
z = numpy.random.rand(3)

#| Here are some plots

x = numpy.linspace(-2,2,1000)
y = x**3
fig, ax = plt.subplots()
ax.plot(x,y)
```

---

#### Transformer son code existant en jupyter-notebook

```bash

(sci-env)$ py2nb myscript.py

```

> Crée un jupyter-notebook de test à destination du chercheur

---

#### Tester le code en ligne

![](binder.png)

---

### Post-traitement

Convertir dans l'autre sens pour les modifications et versionning 

* Nettoyage des cellules
* Ajout des modification dans le code source
* Ajout à la doc 

```
jupyter-nb-convert --to python
jupyter-nb-conert --to markdown
```
---

### Exporter 

jupyter-nbconvert myscript.ipynb --to pdf
jupyter-nbconvert myscript.ipynb --to slides
jupyter-nbconvert myscript.ipynb --to latex

---

### Exporter avec citations 

* On gère les sources grâce à un fichier BibTeX.
* Le style de citation peut être personnalisé grâce un fichier CSL.
* Le tout est ensuite combiné dans Pandoc pour générer un fichier de sortie (Word, PDF, LaTeX, etc.).
`pandoc`
`pandoc-citeproc`
`zotero-betterbibtext`

[Blog Zotero](https://zotero.hypotheses.org/2258#ecrit_academique)

---

## Credits


<small>Largely inspired by</small> <small>[@ixek talk](https://speakerdeck.com/trallard/reproducible-science-the-good-the-bad-the-ugly-and-the-untold)
</small>


