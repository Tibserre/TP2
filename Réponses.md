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

### 3-2 Document your playbook

### 3-3 Document your docker_container tasks configuration.


