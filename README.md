# Kubernetes kurs med JrC

## Steg 1

`kubectl apply -f deployment.yaml`

## Steg 2

Pass på at du har minikube ingress addonen: `minikube addons enable ingress`

Deretter trenger vi en _service_ som definerer de ulike tjenestene en app can tilgjengeligjøre til
verden:

`kubectl apply -f service.yaml`

Nå må vi også ha en _ingress_ som tar et _entrypoint_ og ruter trafikken til servicene vi har i
clusteret:

`kubectl apply -f ingress.yaml`

For å se appen må du kjøre `minikube tunnel <IP>` (IPen får du fra `kubectl get ingress`)
