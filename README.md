
# Projet Conteneurisation et Orchestration - Ynov

## Conteneur
# Creations des images

Lancez la commande suivante pour creer l'image du service lié au projet (applicants-api, identity-api, mssql, redis, rabbitmq)
`docker build projet-nom:v1 fofanad97/projet-nom:v1 d -t projet-nom:v1 .`

Lancez la commande suivante pour chaque image à fin de la tagger
`docker tag projet-nom:v1 fofanad97/projet-nom:v1`

Lancez la commande docker push pour renvoyer les images dans le repository
`docker push projet-nom:v1 fofanad97/projet-nom:v1`

# Voir les images

![screen1](./screenshots/screen1.png)


## Hébergement
AZURE

## Performance



## Bilan de santé

### Vérification des Liveness et readiness probes 
`kubectl describe pod <pod name> -n projet-cloud`

### Vérification des métriques serveur
`kubectl top pods -n projet-cloud`
`kubectl top nodes -n projet-cloud`

### Configurer la redirection de port pour Prometheus
`kubectl port-forward <pod name> 8080:9090 -n projet-cloud`



## Sécurité



## Logs
### Deploiement d'Elastic
`Helm repo add elastic https://helm.elastic.co/ `

#### Installation Elastic Search
`Helm install elasticsearch --namespace=projet-elastic  elastic/elasticsearch --set replicas=1 --set minimumMasterNodes=1 --set clusterHealthCheckParams="wait_for_status=yellow&timeout=1s"`

#### Installation Kibana
`Helm install kibana --namespace=projet-elastic  elastic/kibana`

#### Configurez la redirection de port pour elasticSearch : 
`kubectl port-forward svc/elasticsearch-master -n projet-elastic 9200`

#### Configurez la redirection de port pour Kibana : 
`kubectl port-forward deployment/kibana-kibana -n projet-elastic 5601`

## Déploiement automatisé
#### Installer la chart Helm
`helm install projet ./projet-cloud -n projet-cloud`
#### Desinstaller la chart Helm
`helm uninstall projet -n projet-cloud`

# Projet Conteneurisation et Orchestration - Ynov






## Membres 

- Rodrigo Tapia
- Fofana Djenabou
- Emmanuel Noah


# [Wiki du projet](https://github.com/rorrotapia/m1cloud-projet/wiki)

# [Gestion du Projet](https://github.com/users/rorrotapia/projects/3/views/2)

