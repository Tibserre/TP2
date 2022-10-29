# réponses TP Thibault Serre

## TP1 - Docker
### 1-1 Document your database container essentials: commands and Dockerfile.
- On setup un environnement pour la db (postgres)
- on définit en variables d'environnement son nom, un user et un password
- on crée les tables et on y insère des données

- ici le fichier [Dockerfile DB](./TP1/Database/Dockerfile)

### 1-2 Why do we need a multistage build? And explain each step of this dockerfile.
- utiliser un muultistage build permet que l'image finale soit plus légère, on ne garde que ce qui est utile pour que le docker puisse run. ça évide d'accumuler plein de choses dans le docker qui ne sont utile qu'à l'initialisation, mais pas pour toute la phase de run

- Etape 1 : toutes les dépendances mises à jour grâce à maven
- Etape 2 : run du projet, dans un environnement possédant une JDK

### 1-3 Document docker-compose most important commands. 

- Les commandes les plus importantes sont : 
    - Version (préciser la version de docker)
    - Network pour relier les containers
    - services (ici proxy, DB et API)
    - Volume pour la persistance des données

### 1-4 Document your docker-compose file.
- Etape 1 : création d'un network
- Etape 2 : Run le back, la DB et le proxy 
    - on précise pour chacun le dossier a build, le nom du container une fois build, le réseau pour chacun et, pour certains, s'il faut les restart tant qu'ils ne se sont pas démarrés
- Etape 3 : si ça marche pas, lever la main.

- Ici le fichier [Docker-compose](./TP1/docker-compose.yml)
### 1-5 Document your publication commands and published images in dockerhub.


## TP2 - Github Action

### 2-1 What are testcontainers?
 - Ce sont des containers volatil qu'on utilise pour run des tests unitaires. 
### 2-2 Document your Github Actions configurations.
- 

### 2-3 Document your quality gate configuration.
![hefizobgaeiho](./Imgs/2022-10-25%2015_12_36-simple-api%20-%20tp2takimah%20et%207%20pages%20de%20plus%20-%20Personnel%20%E2%80%93%20Microsoft%E2%80%8B%20Edge.png)
![alt text](./Imgs/2022-10-25%2015_14_48-simple-api%20-%20tp2takimah%20et%208%20pages%20de%20plus%20-%20Personnel%20%E2%80%93%20Microsoft%E2%80%8B%20Edge.png)

## TP3 - Ansible


### 3-1 Document your inventory and base commands
- Dans le dossier inventory, on trouve le fichir de setup. Ce fichier de setup permet, grâce à Ansible, de se connecter a un serveur distant. Dans ce fichier on définit l'user, le chemin pour acceder à la clé privée, et le nom de l'hôte 


### 3-2 Document your playbook
- Dans le dossier rôle, on trouve deux playbook, `playbook.yml` est celui créée lors du td, pour tester. `playbookDocker.yml` est le playbook permettant de lancer tous les rôles.
- Dans `playbookDocker.yml` on retrouve l'ensemble des rôles définis dans Ansible. Cela permet de lancer toutes les tâches dans le bon ordre : Docker > network > proxy > database > app
- Ensuite, dans chacun des dossier de chaque rôle (db, httpd, simple api...) on retrouve le détail des commandes que Ansible doit réaliser.
### 3-3 Document your docker_container tasks configuration.
- On retrouve 8 commandes dans les task pour le role docker.
    1. **clean package** : enlève tous les packages dans le systeme 
    2. **Install device-mapper-persistent-data** permet de donner accès a de l'espace de stockage pour les futurs containers 
    3. **Install lvm2** lvm2 permet gérer le volume physique 
    4. **add repo docker** ajoute un répository docker 
    5. **Install Docker** télécharge docker
    6. **install python3** baahhh installer python 3 du coup
    7. **Pip Install** meme idée, mais cette fois ci changement ! on installe pip
    8. **Make sure Docker is running** on vérifie que docker run, si docker run , toutes les commandes précédentes se sont bien exécutées 
    9. **On est contents**
