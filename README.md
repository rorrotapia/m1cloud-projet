
# Projet Conteneurisation et Orchestration - Ynov

# Conteneur
# Creations des fichiers
`docker build projet-nom:v1 fofanad97/projet-nom:v1 d -t projet-nom:v1 .`
`docker tag projet-nom:v1 fofanad97/projet-nom:v1`
`docker push projet-nom:v1 fofanad97/projet-nom:v1`
# Voir les images


## DEPLOIMENT AUTOMATISE

#### Installer la chart Helm
`helm install projet ./projet-cloud -n projet-cloud`
#### Desinstaller la chart Helm
`helm uninstall projet -n projet-cloud`

## LOGS

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

## Membres 

- Rodrigo Tapia
- Fofana Djenabou
- Emmanuel Noah


# [Wiki du projet](https://github.com/rorrotapia/m1cloud-projet/wiki)

# [Gestion du Projet](https://github.com/users/rorrotapia/projects/3/views/2)

