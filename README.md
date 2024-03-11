# Kubernetes-kurs med JrC

> Velkommen til denne demoen med Kubernetes!
> Her skal vi deploye en enkel docker-app til kubernetes og gjøre den tilgjengelig for omverdenen :)
> For å kunne gjøre dette trenger du `minikube` og `kubectl` installert.

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

Nå kan du åpne http://localhost og se at appen kjører!

## Steg 3

Nå skal vi se på hvor lett det er å skalere opp appen vår i clusteret.

`kubectl scale deployment min-app --replicas 4`

Kjør `kubectl get pods` så ser vi at vi har 4 kopier av appen vår kjørende

Prøv å refreshe siden nå og se at navnet vil bytte mellom de fire _podsa_ som appen din kjører
på.

> [!TIP]
> Ser du hvilken strategi kubernetes bruker for load-balancing? (load-balancing = fordeling av
> arbeid på tilgjengelige ressurser.)

_Når du er ferdig med alle stagene kan du hoppe over til [DEL
2](https://github.com/progitas/kubernetes-kurs/tree/del-2)_
