
# Projet Conteneurisation et Orchestration - Ynov
#### Membres (Rodrigo Tapia - Fofana Djenabou - Emmanuel Noah)

## 1. Docker
#### a. Création des images
Lancez la commande suivante pour creer l'image du service lié au projet (applicants-api, identity-api, mssql, redis, rabbitmq)
```
docker build projet-nom:v1 fofanad97/projet-nom:v1 d -t projet-nom:v1 .
```

Lancez la commande suivante pour chaque image à fin de la tagger
```
docker tag projet-nom:v1 fofanad97/projet-nom:v1
```

#### b. Mise en ligne des images
Lancez la commande docker push pour renvoyer les images dans le repository
```
docker push projet-nom:v1 fofanad97/projet-nom:v1
```

## 2. Kubernetes
#### a. Création des manifests

#### b. Création des resources sur Kubernetes
Placez vous dans le répertoire des manifests, puis lancez les commandes correspondantes
```
kubectl create -f NAMEFILE
kubectl delete -f NAMEFILE
kubectl apply -f NAMEFILE
```

#### c. Performance


#### d. Affinités


#### e. Installation d'un Ingress controller
```
kubectl create namespace NAMESPACE
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm install nginx-ingress ingress-nginx/ingress-nginx --namespace NAMESPACE --create-namespace --set controller.replicaCount=2 --set controller.nodeSelector."kubernetes\.io/os"=linux
```


## 3. Bilan de santé

#### a. Vérification des Liveness et readiness probes 
```kubectl describe pod <pod name> -n projet-cloud```

#### b. Vérification des métriques serveur
```kubectl top pods -n projet-cloud```
```kubectl top nodes -n projet-cloud```

#### c. Configurer la redirection de port pour Prometheus
```kubectl port-forward <pod name> 8080:9090 -n projet-cloud```



## 4. Sécurité



## 5. Mise en place d'un gestion de logs avancé
Afin de pouvoir les exploiter correctement les logs .
#### a. Télechargerment du repo elastic
```
helm repo add elastic https://helm.elastic.co/

```

#### c. Installation Elastic Search et Kibana
```
helm install elasticsearch --namespace=projet-elastic  elastic/elasticsearch --set replicas=1 --set minimumMasterNodes=1 --set clusterHealthCheckParams="wait_for_status=yellow&timeout=1s"
helm install kibana --namespace=projet-elastic  elastic/kibana
```


#### d. Configurez la redirection de port pour elasticSearch : 
`kubectl port-forward svc/elasticsearch-master -n projet-elastic 9200`

#### e. Configurez la redirection de port pour Kibana : 
`kubectl port-forward deployment/kibana-kibana -n projet-elastic 5601`

![ElasticSearch](./screenshots/elastic-search.JPG)


## 5. Déploiement automatisé
#### a. Installation du chart Helm
Lancez la commande suivante pour installer le projet

`helm install projet ./projet-cloud -n projet-cloud`

Lancez la commande suivante pour desinstaller

`helm uninstall projet -n projet-cloud`

#### b. Fichiers manifests
Le chart contient principalement les éléments suivants:

- un fichier *Chart.yaml* qui définit les metadata du projet,
- des ficchiers manifests *deploy.yaml* *service.yaml* *ingress.yaml*  utilisé pour la création des resources
- un fichier *values.yaml* utilisé pour substituer les variables par des valeurs dynamiques
- un fichier *NOTES.txt* qui donne des informations à la création de la release

```
$ cd projet-cloud
$ tree manifests
manifests
├── deploy.yaml
├── ingress.yaml
├── service.yaml
```



# [Wiki du projet](https://github.com/rorrotapia/m1cloud-projet/wiki)

# [Gestion du Projet](https://github.com/users/rorrotapia/projects/3/views/2)

