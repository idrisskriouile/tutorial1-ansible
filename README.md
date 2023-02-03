# tutorial1-ansible
Ansible est un outil de configuration et de déploiement de logiciels qui utilise des scripts appelés "playbooks" pour décrire les tâches à exécuter sur des serveurs distants. Il est écrit en Python et utilise SSH pour se connecter aux serveurs.
Pour installer Ansible sur un système Ubuntu ou Debian, utilisez la commande suivante:
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible
Pour vérifier la version d'Ansible installée, utilisez la commande suivante:
ansible --version
Pour créer un inventaire (liste des serveurs à gérer), vous pouvez utiliser la commande suivante pour créer un fichier hosts dans le répertoire de travail courant:
echo "server1 ansible_host=192.168.1.100 ansible_user=root" >> hosts
Pour tester la connexion à un serveur spécifique dans l'inventaire, utilisez la commande suivante:
ansible -m ping server1
Pour exécuter une tâche spécifique sur un serveur, utilisez la commande suivante:
ansible server1 -m command -a "apt-get update"
Pour exécuter un playbook, utilisez la commande suivante:
ansible-playbook -i hosts playbook.yml
Il existe de nombreuses autres commandes et options disponibles, mais cela devrait vous donner une idée de la façon dont Ansible fonctionne. Il est recommandé de consulter la documentation officielle pour en savoir plus sur les fonctionnalités avancées et les meilleures pratiques d'utilisation d'Ansible.
Ansible utilise un concept appelé "modules" pour effectuer des tâches sur les serveurs distants. 
Les modules sont des scripts préécrits qui peuvent être utilisés pour exécuter des commandes, installer des paquets, gérer des services, etc. Il existe de nombreux modules Ansible intégrés pour effectuer des tâches courantes, mais vous pouvez également écrire vos propres modules si nécessaire.




# Voici quelques exemples concrets d'utilisation d'Ansible pour différentes tâches courantes :
**Installation de paquets** : Vous pouvez utiliser les modules apt ou yum pour installer des paquets sur des serveurs distants. Par exemple, pour installer Nginx sur tous les serveurs de votre inventaire, vous pouvez utiliser la commande suivante :
```yaml
# Code Ansible
- ansible all -m apt -a "name=nginx state=present"
```


**Configuration de serveurs** : Vous pouvez utiliser des modules tels que lineinfile ou template pour configurer des fichiers de configuration sur les serveurs distants. Par exemple, pour configurer Nginx pour désactiver les en-têtes de serveur sur tous les serveurs, vous pouvez utiliser la commande suivante :
```yaml
# Code Ansible
ansible all -m lineinfile -a "dest=/etc/nginx/nginx.conf line='server_tokens off;'"

Déploiement d'applications : Vous pouvez utiliser des modules tels que git ou svn pour déployer des applications sur des serveurs distants. Par exemple, pour déployer une application à partir d'un dépôt git sur tous les serveurs, vous pouvez utiliser la commande suivante:
ansible all -m git -a "repo=https://github.com/example/app.git dest=/var/www/app"
Exécution de scripts : Vous pouvez utiliser le module command ou script pour exécuter des scripts sur des serveurs distants. Par exemple, pour exécuter un script de sauvegarde sur tous les serveurs, vous pouvez utiliser la commande suivante:
ansible all -m script -a "backup.sh"
Gestion de services : Vous pouvez utiliser le module service pour gérer les services sur les serveurs distants. Par exemple, pour redémarrer un service sur tous les serveurs, vous pouvez utiliser la commande suivante:
ansible all -m service -a "name=nginx state=restarted"
Gestion des utilisateurs : Vous pouvez utiliser le module user pour gérer les utilisateurs sur les serveurs distants. Par exemple, pour créer un utilisateur sur tous les serveurs, vous pouvez utiliser la commande suivante:
ansible all -m user -a "name=newuser state=present"
Gestion des groupes : Vous pouvez utiliser le module group pour gérer les groupes sur les serveurs distants. Par exemple, pour ajouter un utilisateur à un groupe sur tous les serveurs, vous pouvez utiliser la commande suivante:
ansible all -m group -a "name=sudo state=present members=newuser"
Copie de fichiers : Vous pouvez utiliser le module copy pour copier des fichiers sur les serveurs distants. Par exemple, pour copier un fichier local sur tous les serveurs, vous pouvez utiliser la commande suivante:
ansible all -m copy -a "src=local_file.txt dest=/remote/path"
Gestion des paquets : Vous pouvez utiliser les modules apt ou yum pour gérer les paquets sur les serveurs distants. Par exemple, pour mettre à jour tous les paquets sur les serveurs, vous pouvez utiliser la commande suivante:
ansible all -m apt -a "name=* state=latest"
Exécution de commandes shell : Vous pouvez utiliser le module shell pour exécuter des commandes shell sur les serveurs distants. Par exemple, pour vérifier l'espace disque sur tous les serveurs, vous pouvez utiliser la commande suivante:
ansible all -m shell -a "df -h"


Ansible est un outil très puissant et flexible, il est donc important de consulter la documentation officielle pour en savoir plus sur les fonctionnalités avancées et les meilleures pratiques d'utilisation. Il est également possible de combiner ces tâches dans des playbooks pour automatiser des processus plus complexes.
Gestion des clés ssh : Vous pouvez utiliser le module authorized_key pour gérer les clés ssh sur les serveurs distants. Par exemple, pour ajouter une clé ssh à un utilisateur sur tous les serveurs, vous pouvez utiliser la commande suivante:
ansible all -m authorized_key -a "user=newuser key='ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC2...'"
Gestion des packages python: Vous pouvez utiliser le module pip pour gérer les packages python sur les serveurs distants. Par exemple, pour installer un package sur tous les serveurs, vous pouvez utiliser la commande suivante:
ansible all -m pip -a "name=packagename version=x.x.x"
Gestion des bases de données : Vous pouvez utiliser les modules mysql_db ou postgresql_db pour gérer les bases de données sur les serveurs distants. Par exemple, pour créer une base de données sur un serveur, vous pouvez utiliser la commande suivante:
ansible server1 -m mysql_db -a "name=newdb state=present"
Gestion de la sécurité : Vous pouvez utiliser des modules tels que firewalld ou ufw pour gérer les pare-feux sur les serveurs distants. Par exemple, pour ouvrir un port sur un serveur, vous pouvez utiliser la commande suivante:
ansible server1 -m firewalld -a "port=80/tcp state=enabled"
Gestion des certificats : Vous pouvez utiliser des modules tels que acme_certificate ou openssl_certificate pour gérer les certificats sur les serveurs distants. Par exemple, pour générer un certificat pour un domaine sur un serveur, vous pouvez utiliser la commande suivante:
ansible server1 -m acme_certificate -a "name=example.com"
Gestion des fichiers et répertoires : Vous pouvez utiliser les modules file ou synchronize pour gérer les fichiers et les répertoires sur les serveurs distants. Par exemple, pour créer un répertoire sur tous les serveurs, vous pouvez utiliser la commande suivante:
ansible all -m file -a "path=/path/to/new_folder state=directory"
Gestion des modules Apache : Vous pouvez utiliser le module apache2_module pour gérer les modules Apache sur les serveurs distants. Par exemple, pour activer un module sur tous les serveurs, vous pouvez utiliser la commande suivante:
ansible all -m apache2_module -a "name=rewrite state=present"
Gestion des utilisateurs et des groupes sur Windows : Vous pouvez utiliser les modules win_user et win_group pour gérer les utilisateurs et les groupes sur les serveurs Windows distants. Par exemple, pour créer un utilisateur sur un serveur Windows, vous pouvez utiliser la commande suivante:
ansible windows-server -m win_user -a "name=newuser password=P@ssword123 state=present"
Gestion des services Windows : Vous pouvez utiliser le module win_service pour gérer les services sur les serveurs Windows distants. Par exemple, pour démarrer un service sur un serveur Windows, vous pouvez utiliser la commande suivante:
ansible windows-server -m win_service -a "name=Spooler state=started"
Gestion de la sécurité des fichiers : Vous pouvez utiliser le module acl pour gérer les autorisations des fichiers sur les serveurs distants. Par exemple, pour donner à un utilisateur la possibilité de lire un fichier sur un serveur, vous pouvez utiliser la commande suivante:
ansible server1 -m acl -a "path=/path/to/file owner=newuser mode=r"
Gestion des réseaux : Vous pouvez utiliser les modules ios_command, nxos_command, eos_command pour gérer les équipements de réseau (routeurs, commutateurs) sur les serveurs distants. Par exemple, pour vérifier l'état de l'interface sur un équipement, vous pouvez utiliser la commande suivante:
ansible switch -m ios_command -a "commands='show interface status'"
Gestion des containers : Vous pouvez utiliser les modules docker_container, podman_container pour gérer les containers sur les serveurs distants. Par exemple, pour démarrer un container sur un serveur, vous pouvez utiliser la commande suivante:
ansible server1 -m docker_container -a "name=mycontainer state=started"
Gestion des provisioning : Vous pouvez utiliser les modules vmware_guest, k8s pour gérer les machines virtuelles et les clusters Kubernetes sur les serveurs distants. Par exemple, pour créer une VM sur un serveur, vous pouvez utiliser la commande suivante:
ansible vcenter -m vmware_guest -a "name=myvm state=present folder=myfolder"
Gestion de la sécurité : Vous pouvez utiliser les modules openscap, lynis pour gérer la sécurité sur les serveurs distants. Par exemple, pour vérifier les vulnérabilités sur un serveur, vous pouvez utiliser la commande suivante:
ansible server1 -m openscap -a "scan_type=cron"
Gestion de la performance : Vous pouvez utiliser les modules prometheus, grafana pour gérer la performance sur les serveurs distants. Par exemple, pour configurer un serveur pour collecter des métriques, vous pouvez utiliser la commande suivante:
ansible server1 -m prometheus -a "state=present"
Gestion des certificats SSL : Vous pouvez utiliser les modules acme_certificate, letsencrypt pour gérer les certificats SSL sur les serveurs distants. Par exemple, pour obtenir un certificat SSL pour un domaine, vous pouvez utiliser la commande suivante:
ansible server1 -m acme_certificate -a "name=example.com account_key_src=/path/to/account.key"
Gestion des archives : Vous pouvez utiliser les modules unarchive, archive pour gérer les archives (tar, zip, etc) sur les serveurs distants. Par exemple, pour décompresser un fichier archive sur un serveur, vous pouvez utiliser la commande suivante:
ansible server1 -m unarchive -a "src=/path/to/archive.tar.gz dest=/path/to/extract"
Gestion des rôles : Vous pouvez utiliser les rôles Ansible pour organiser et partager les tâches communes. Les rôles sont des collections de tâches, variables, fichiers de modèles, etc. qui peuvent être réutilisés dans plusieurs playbooks. Par exemple, pour utiliser un rôle pour installer un serveur web, vous pouvez utiliser la commande suivante :
ansible-playbook -i inventory.ini site.yml -l webserver --ask-become-pass
Gestion de l'orchestration : Vous pouvez utiliser les modules async_status et async_poll pour gérer l'orchestration des tâches avec Ansible. Ces modules permettent de lancer des tâches en parallèle et de surveiller leur progression. Par exemple, pour lancer une tâche de mise à jour de paquet en parallèle sur plusieurs serveurs et surveiller l'état de cette tâche, vous pouvez utiliser les commandes suivantes :
ansible all -m async_status -a "jid={{ async_task.ansible_job_id }}"
ansible all -m async_poll -a "jid={{ async_task.ansible_job_id }}"
Gestion des Inventory : Vous pouvez utiliser les inventaires dynamiques d'Ansible pour gérer les serveurs distants de manière dynamique. Les inventaires dynamiques permettent de générer automatiquement la liste des serveurs distants à partir d'une source externe (script, cloud, etc.). Par exemple, pour utiliser un inventaire dynamique pour gérer les serveurs AWS, vous pouvez utiliser la commande suivante :
ansible all -i aws_ec2.py -m ping
