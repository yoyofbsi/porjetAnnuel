# Préparation de l'inventaire des serveurs

Préparation des 4 groupes principaux

<br>

Dans un premier temps nous allons insérer **les serveurs de load-balancing**. 

Avec leur nom, leur IP, leur utilisateur Ansible.

Et nous choisiront le serveur principal en lui ajoutant "primary=yes"

```
[haservers]
nom_du_serveurs ansible_host=<IP_du_serveur> ansible_user=<ssh_user> primary=yes
nom_du_serveurs ansible_host=<IP_du_serveur> ansible_user=<ssh_user>
...
```
<br>

Nous continuerons avec **les serveurs Web** :

Avec seulement leur nom, leur IP, leur utilisateur Ansible.
```
[webservers]
nom_du_serveurs ansible_host=<IP_du_serveur> ansible_user=<ssh_user>
nom_du_serveurs ansible_host=<IP_du_serveur> ansible_user=<ssh_user>
```

<br>

Un point particulier est l'implémentation des **loadbalancer SQL**.

Pour l'instant ils seront considéré sur les mêmes serveurs que les serveurs Web.
```
[proxysql:children]
webservers
```

<br>

La dernière partie implémente **les serveurs SQL**.

Comme pour les autres ils faut définir leur nom, leur IP, leur utilisateur Ansible.

Et la variable "mysql_slave_of" devra être ajouté sur les serveurs Slave afin de définir l'IP du master.
```
[dbservers]
nom_du_serveurs ansible_host=<IP_du_serveur> ansible_user=<ssh_user>
nom_du_serveurs ansible_host=<IP_du_serveur> ansible_user=<ssh_user> mysql_slave_of=<IP_du_serveur_primaire>
nom_du_serveurs ansible_host=<IP_du_serveur> ansible_user=<ssh_user> mysql_slave_of=<IP_du_serveur_primaire>
```

<br>

**Exemple :**
```
[haservers]
haservers01 ansible_host=<IP> ansible_user=ansible primary=yes
haservers02 ansible_host=<IP> ansible_user=ansible

[webservers]
webservers01 ansible_host=<IP> ansible_user=ansible
webservers02 ansible_host=<IP> ansible_user=ansible

[proxysql:children]
webservers

[dbservers]
dbservers01 ansible_host=<IP> ansible_user=ansible
dbservers02 ansible_host=<IP> ansible_user=ansible mysql_slave_of=<IP>
dbservers03 ansible_host=<IP> ansible_user=ansible mysql_slave_of=<IP>
```
