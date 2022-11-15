> Les fichiers sont TRES certainement a modifier.   
> Je n'ai fais aucun test sur toutes les configurations.  
> certains lien/noms sont modifié / remplir. 
> Le fichier script/prepare.sh est a Faire sur le gitlab des dependances.  



# Docker

Il existes plusieurs Dockerfile.

## docker automatisation

Les premier `Dockerfile-automatisation` va preparer l'environement de l'automates, installer git, python et installer les dependances de la librairie.

Pour build l'image:  
 - `docker build -t automatisation:<TAG> -f Dockerfile-automatisation .`   

Pour run l'image (dans notre cas inutile.)  
`docker run automatisation:<TAG>`  



## docker automate
Il faut apres avoir build l'image automatisation build l'image de l'automate.

TODO:
Faire un choix. 
> soit on utilise une seul image automate

et donc pour run une image on fait `docker run automate:308`
ou 308 est le tag de automate. MAIS si on fait 
`docker run automate`
il va run le dernier automate build... déliquat. 

 - `docker build -t automate:308 -f Dockerfile-automatisation . `

L'autre solution serait de build une image par automate.
> Chaque automate possède une image docker.

`docker run automate-308`  
`docker run automate-308:latest`  
`docker run automate-308:15-11-2022`  
`docker run automate-308:<TAG>`  

dans ce cas la il faut build via cette commande:  
 - `docker build -t automate-308:15-11-2022 -f automates/Dockerfile308 . `



# Déploiement 

> J'ai choisi d'utiliser les docker-compose.   
> Facile, Rapide, Prérenne.

Pour build un automate:  
 - `docker-compose up -d -f docker-compose/docker-compose-308.yml`

Il est possible de lancer l'automate directement via la commande:
 - `docker run --name Automate308 -v ./local-file/automate-308:/automate/ automate:308`

# Pense bête docker:
_______
Affiche les dockers qui sont *en fonctionnement*.
`docker ps`  
permet d'afficher TOUS les dockers allumé ou coupé.  
`docker ps -a` 
Pour supprimer un docker :   
`docker rm -f`   
Pour stoper un docker qui fonctionne:  
`docker stop id_container`  
`docker stop container_name`   
Pour start un docker:  
`docker start id_container`  
`docker start container_name`  
Telecharger une image:  
`docker pull nom-image:tag`  
Si aucun tag spécifié par défaut (latest)  
_______