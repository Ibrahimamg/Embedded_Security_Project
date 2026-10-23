# Attack the Vault
 
Attaque par canal auxiliaire sur un coffre à mot de passe, avec une
ChipWhisperer-Nano, puis contre-mesure à temps constant. La cible est un Arduino Uno (ATmega328P).
 
## Organisation du dépôt
 
- Le **rapport complet** (write-up) est dans le
  **[wiki](https://github.com/Ibrahimamg/Embedded_Security_Project/wiki)**.
- Le **code** est ici, rangé par dossier :
  - `notebooks/` : les notebooks Jupyter (attaque SPA et contre-mesure).
  - `firmware/` : le firmware de la cible (version vulnérable, version durcie) et `gpio-tristate.c`.
## Prérequis
 
- Une **ChipWhisperer-Nano** et le paquet Python `chipwhisperer`.
- La cible : un **Arduino Uno** (ATmega328P). Pour la mesure, la puce est sortie de l'Uno et montée
  sur breadboard avec un shunt sur sa ligne d'alimentation.
- Pour flasher le firmware : l'IDE Arduino avec la bibliothèque **Crypto** de Rhys Weatherley (pour le
  hash SHA3).
## Lancer l'attaque
 
1. Monter le banc et brancher la Nano directement sur un port USB du PC (éviter les hubs).
2. Flasher la cible avec `firmware/secure_sketch.ino`.
3. Ouvrir `notebooks/attaque_spa.ipynb` et exécuter les cellules : l'attaque récupère le mot de passe
   caractère par caractère, puis affiche la preuve (`ACCESS GRANTED`, salt, hash).
4. Pour la contre-mesure, flasher `firmware/secure_sketch_durci.ino` et relancer
   `notebooks/contre_mesure.ipynb` : la fuite a disparu.
## Auteur
 
Ibrahim Amghar
