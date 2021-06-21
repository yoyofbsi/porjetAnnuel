# **Préparation avant déploiement**

Condition requises :
- Ansible 2.10 (minimum)
- Avoir minimum 7 serveurs avec une configuration réseau fonctionnelle 

A faire sur chacun des serveurs :
- apt install sudo
- adduser ansible
- usermod -aG sudo ansible
- vim /etc/sudoers
  - ansible    ALL=(ALL:ALL)
  
A faire sur le serveur Ansible :
- ssh-keygen
- ssh-copy-id ansible@*ip-serveur*         (Faire ça pour chaque serveur de l'inventaire)
- Lancer l'installation des prérequis (requirements.yml)
  - ansible-galaxy install -r projetAnnuel/roles/requirements.yml
