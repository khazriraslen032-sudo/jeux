# 🎯 Jeu de Stratégie en C (Cache-Cache / Grille 9x9)

Un mini-jeu console interactif développé en **langage C** pour deux joueurs, axé sobre la tactique, le calcul de coordonnées et la gestion des points de vie.

## 🕹️ Règle du jeu & Fonctionnement
- **Mode de jeu :** Multijoueur local (2 joueurs).
- **Grille :** Une matrice de $9 \times 9$ initialisée avec des cellules sécurisées ('V').
- **Mécanique :** 
  1. Un joueur choisit secrètement une position (cachette).
  2. L'autre joueur tente de deviner et de chercher cette position.
  3. Chaque joueur commence avec **3 points de vie**. En cas de réussite, l'adversaire perd un point et la ligne/colonne correspondante est pénalisée ('F').
- **Fin du partie :** Le jeu continue jusqu'à l'épuisement des points d'un joueur, suivi d'une animation finale avec un cœur ASCII coloré et l'annonce du gagnant.

## 🛠️ Caractéristiques techniques
- Utilisation de tableaux bidimensionnels en C.
- Gestion des couleurs dans la console via **les codes d'échappement ANSI** (`\x1b[32m`, `\x1b[31m`).
- Utilisation de fonctions aléatoires (`srand`, `rand`) pour déterminer de manière aléatoire quel joueur commence.
- Effets visuels de transition (`system("cls")`, `sleep`).

## ⚙️ Compilation et Exécution
Pour compiler et lancer le jeu sous Linux/Windows (avec GCC) :
```bash
gcc main.c -o jeu_strategie
./jeu_strategie
