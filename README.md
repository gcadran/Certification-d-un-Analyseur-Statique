# TP67 — Analyseur statique pour le langage bilbo

Master 1 Informatique – ACF (Analyse & Conception Formelle)
Auteurs : Guilherm CADRAN – Gwendal CARIOU 

## Objectif

Ce dépôt contient un travail de projet visant à concevoir, prouver et intégrer un analyseur statique pour un petit langage impératif nommé `bilbo`.
Le but principal : garantir qu'un programme accepté par l'analyseur ne pourra jamais exécuter `exec(0)` (instruction dangereuse).

La chaîne de travail est : spécification et preuve en Isabelle/HOL → génération Scala 

## Contenu du dépôt

- `tp67.thy` — théorie Isabelle : grammaire du langage, évaluateur, et analyseurs (`san0` .. `sanX`).
- `TP67_ACF/` — projet Scala (généré et intégré) : code de l'analyseur exporté et l'interpréteur.
  - `src/main/scala/tp67/` — sources Scala (analyseur, interpréteur, CLI).
  - `tests/` ou fichiers `ok*.txt` / `bad*.txt` — programmes `bilbo` pour tests.


## Le langage `bilbo` (résumé)

- Expressions : constantes, variables, addition, soustraction.
- Conditions pour les commandes `if`.
- Instructions : `read`, `print`, `Aff` (affectation), `Seq` (séquence), `If`, `Skip`.
- Instruction critique : `exec(e)` — dangereuse si `e` peut être 0.

Un programme est dangereux si, pour certaines entrées, il peut exécuter `exec(0)`.

## Analyseurs implémentés

Les versions successives d'analyseur sont fournies dans la théorie Isabelle et exportées en Scala :

- `san0` : rejette tout programme contenant une instruction `exec`.
- `san1` : accepte si toutes les expressions passées à `exec` sont des constantes non-nulles.
- `san2` : propagation d'informations, vérifie si `exec(e)` peut évaluer à 0.
- `san3`, `san4`, ... : raffinements successifs pour améliorer précision/sécurité.

Dans le code Scala généré, la fonction utilisée dans l'intégration s'appelle typiquement `san4` (ou la version choisie) ; l'adaptateur `Analyzer.safe` délègue vers cette fonction.

## Compilation et exécution

Pré-requis : Java (JDK 11+ recommandé), sbt (1.4+ ou version installée dans l'environnement).




Pour lancer l'application (si un `Main` est présent et configuré dans `build.sbt`) :

```powershell
sbt run
```

Si le projet possède des tests sbt :

```powershell
sbt test
```

Remarque : le projet fourni contient des sources générées depuis Isabelle — la compilation peut produire des `warnings` (p. ex. code unreachable) qui sont attendus et sans impact sur la sécurité.

## Utilisation de l'analyseur (API)

Dans `src/main/scala/tp67/Analyzer.scala` se trouve un simple wrapper exposant la fonction :

```scala
object Analyzer {
  def safe(p: statement): Boolean = {
    // délègue à la version choisie de l'analyseur (ex. san4)
  }
}
```

- `true` signifie "sécurisé" (aucune exécution possible de `exec(0)` selon l'analyse).
- `false` signifie "potentiellement dangereux" (l'analyse n'a pas pu exclure `exec(0)`).

## Tests manuels

Des exemples de programmes `bilbo` sont fournis dans le répertoire racine (`ok*.txt`, `bad*.txt`). Pour tester manuellement :

- Charger un fichier dans l'interpréteur CLI (ou appeler la fonction d'analyse dans `Main`) et vérifier la sortie.

Si vous voulez des scripts pour exécuter tous les tests automatiquement, je peux en ajouter un (PowerShell ou sbt task) qui exécute l'analyseur sur chaque fichier et affiche un résumé.



