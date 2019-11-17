# PIEscaped 2019.1
VMware version of EPITA's PIE (Archlinux i3) with compatibility patches
![](https://raw.githubusercontent.com/abrvham/PIEscaped/master/illustration.png)
## Information
PIEscaped est une version VMware du système d'exploitation du PIE en 2019-2020 (ArchLinux i3-wm), avec plusieurs patchs de compatibilité (et un script de push moulinette).

Tous les paquets ont été downgradés (y compris le kernel et la libc) pour correspondre à leur version dans l'état de l'image du PIE tel que défini par le CRI ([voir ici](https://static.cri.epita.fr/pie/pkg-ver.html)).

Open-vm-tools est pré-installé.
Testé avec VMware Fusion 11.5

## Patchs
#### 1) Patchs concernant la compatibilité *Open-vm-tools/ArchLinux*
- Patch d'un problème empêchant le copier-coller Host<->Guest
- Patch d'un problème empêchant le fonctionnement du service vmtoolsd au redémarrage de la VM (= résolution d'affichage non dynamique)
- Ajout d'une commande pour mount l'*HGFS* (qui ne se fait pas avec Archlinux)

#### 2) Patchs des paquets d'EPITA
- Epita-themes-sddm 1.0-2: correction de variables non définies et utilisées (logo/version)
- i3lock: Suppression d'un appel à un service à la sortie d'i3lock, et non présent dans PIEscaped ([voir fork](https://github.com/abrvham/i3lock-PIEscaped/))

## Download and installation
1) Téléchargez le fichier .zip à l'adresse https://dealzy.io/piescaped
2) Dézippez et ouvrez le fichier PIEscaped.vmx
3) Pour autoriser le partage de dossiers host/guest, [voir la doc VMware](https://docs.vmware.com/fr/VMware-Fusion/8.0/com.vmware.fusion.using.doc/GUID-7F068DD6-4F3D-4B3C-B468-81AA9C43A197.html)

## Usage
- Login/password:
  *root/epita*
  *layer8/epita*
- Pour mount vos dossiers partagés, avec un terminal:
  <pre>dmnt</pre>
  Vos dossiers sont ensuite disponibles dans le dossier *afs*

- Pour push-tags vers la moulinette, allez dans le dossier à push puis: 
  <pre>mouli *</pre>
  avec * un identifiant de tag. Cette commande va automatiquement commit, créer un tag "submission/CURRDIR-* ", puis push.
  
## Information
Certains paquets non nécéssaires (ex Gimp) du PIE sont volontairement absents de PIEscaped afin de réduire la taille du volume. Ils peuvent cependant être installés à tout moment avec pacman. **Leur version sera alors automatiquement la même que celle du PIE**. Si vous pensez qu'il devrait être installé de base, ouvrez un ticket.
Deux trois autres paquets sont présents sur PIEscaped et ne le sont pas sur le PIE (exemple: lldb, gtkmm3). Ils ont été installés pour permettre la compatibilité avec VMware ou car ces paquets peuvent être utile. Tous les paquets installés sur PIEscaped sont visibles dans le fichier *pkg* du repo 

PIEscaped n'est pas un dump du PIE, c'est une version d'ArchLinux dont le but est d'être le plus semblable possible aux machines du campus.

## Changelog
**2019.1** (17.11.19): initial version
