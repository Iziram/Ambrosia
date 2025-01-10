# Où les utiliser ?

<pre v-click style="font-size:0.5rem;">

| Famille d'Adresses   | Environnement d'Exécution                     | Exemple de Technologie Utilisant l'AF                       |
|----------------------|-----------------------------------------------|-------------------------------------------------------------|
| **AF_INET**          | Réseau (IPv4)                                 | HTTP (serveurs web, ex. Nginx, Apache)                      |
|                      | - Communication sur des réseaux locaux ou     |                                                             |
|                      | étendus (LAN/WAN).                            |                                                             |
|                      | - Transmission de données via TCP/UDP.        |                                                             |
|                      | - Utilisé par les applications réseau,        |                                                             |
|                      | clients et serveurs distants.                 |                                                             |
| -------------------- | --------------------------------------------  | ----------------------------------------------------------- |
| **AF_UNIX**          | Système local (Communication inter-processus) | Sockets pour Docker daemon                                  |
|                      | - Communication rapide et sécurisée entre     |                                                             |
|                      | processus sur la même machine.                |                                                             |
|                      | - Utilise des fichiers spéciaux pour les      |                                                             |
|                      | sockets dans le système de fichiers.          |                                                             |
|                      | - Idéal pour les systèmes de gestion de       |                                                             |
|                      | services comme Docker, où la communication    |                                                             |
|                      | locale est essentielle.                       |                                                             |
| -------------------- | --------------------------------------------  | ----------------------------------------------------------- |
| **AF_VSOCK**         | Virtualisation (Communication VM-hyperviseur) | Virtio-VSOCK pour QEMU/KVM                                  |
|                      | - Permet la communication directe entre       |                                                             |
|                      | des machines virtuelles et leurs              |                                                             |
|                      | hyperviseurs sans passer par le réseau        |                                                             |
|                      | traditionnel.                                 |                                                             |
|                      | - Utilisé dans des environnements virtualisés |                                                             |
|                      | (comme QEMU, VMware) pour la gestion et       |                                                             |
|                      | la communication interne.                     |                                                             |
|                      | - Évite l'utilisation d'adresses IP et        |                                                             |
|                      | de configurations réseau complexes pour       |                                                             |
|                      | les communications internes.                  |                                                             |


</pre>

---

## Démo (Yay du mouvement)