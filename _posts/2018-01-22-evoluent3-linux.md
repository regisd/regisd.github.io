title: Evoluent VerticalMouse 3 under Linux
date: 2017-11-26T17:12:00+01:00
categories:
  - Hightech
tags:
  - Linux
---
J'ai une souris Evoluent VerticalMouse 3, et à chaque fois je galère un peu pour avoir un mapping des boutons qui me convienne.

Donc voici le fichier `/usr/share/X11/xorg.conf.d/90-evoluent.conf` qui me convient.

https://gist.github.com/regisd/da23e10bcd87bb66f8a9b97ef0cf5f3a

```
Section "InputClass"
  Identifier "Evoluent VerticalMouse 3"
  # Change id to what lsusb returns for the mouse
  MatchUSBID "1a7c:0068"
  Option "ButtonMapping" "1 2 3 4 5 6 7 8 9 10 11 12 13 14"
EndSection
```

Sous Linux, la signification des boutons est la suivante:
1. Click gauche
2. Click droit
3. Click milieu
4. Wheel haut
5. Wheel bas
6. ?
7. ?
8. Retour
9. Click wheel
