# Docker

Il existes plusieurs Dockerfile.

## docker automatisation

Les premier `Dockerfile-automatisation` va preparer l'environement de l'automates, installer git, python et installer les dependances de la librairie.

Pour build l'image:
`docker build -t automatisation:<TAG> -f Dockerfile-automatisation .`
Pour run l'image (dans notre cas inutile.)
`docker run automatisation:<TAG>`



## docker automate
> Chaque automate possède une image docker.

Il faut apres avoir build l'image automatisation build l'image de l'automate.

TODO:
Faire un choix. soit utilise une seul image automate

et donc pour run une image on fait `docker run automate:308`
ou 308 est le tag de automate. MAIS si on fait 
`docker run automate`
il va run le dernier automate build... déliquat. 

`docker build -t automate:308 -f Dockerfile-automatisation . `

L'autre solution serait de build une image par automate.


`docker run automate-308`
`docker run automate-308:latest`
`docker run automate-308:15-11-2022`
`docker run automate-308:<TAG>`

dans ce cas la il faut build via cette commande:
`docker build -t automate-308:15-11-2022 -f automates/Dockerfile308 . `