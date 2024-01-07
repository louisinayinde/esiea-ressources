# Guide d'Utilisation du Projet esiea-ressources
Étapes pour Déployer le Projet
## 1. Cloner le repository Git
**git clone https://github.com/louisinayinde/esiea-ressources.git**
## 2. Se placer dans le dossier du projet
**cd esiea-ressources**
## 3. Lancer le build des images
**docker-compose -f docker-compose.build.yml build**
## 4. Préparer l'Exposition de l'Application
Création du registre \
**docker run -d -p 5000:5000 --name registry registry:2.7** \
Création des tags \
**docker tag esiea-ressources_vote:latest localhost:5000/esiea-ressources_vote:latest** \
**docker tag esiea-ressources_worker:latest localhost:5000/esiea-ressources_worker:latest** \
**docker tag esiea-ressources_seed-data:latest localhost:5000/esiea-ressources_seed-data:latest** \
**docker tag esiea-ressources_result:latest localhost:5000/esiea-ressources_result:latest** \
Push des images builds dans le registre \
**docker push localhost:5000/esiea-ressources_vote:latest** \
**docker push localhost:5000/esiea-ressources_worker:latest** \
**docker push localhost:5000/esiea-ressources_seed-data:latest** \
**docker push localhost:5000/esiea-ressources_result:latest** \
Vérification des builds dans le registre \
**curl http://localhost:5000/v2/_catalog** \
## 5. Déployer le projet
**docker compose up**
