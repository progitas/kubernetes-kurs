# Kubernetes kurs med JrC

# Del 2

Hurra! Teamet vårt har jobbet bra og er klare med en ny versjon av appen vår :strong:.
Som DevOps ansvarlig er det nå vår jobb å oppgradere til den nye versjonen av appen :)

> Som du kanskje ser så har vi steppet opp infrastrukturen vår, som nå har to _miljøer_ og bruker
> **kustomize** for å gjenbruke konfigurasjonen på tvers av miljøene.

> For å deploye hele miljøet kan du bruke kommandoen `kubectl apply -k overlays/staging`

> [!WARNING]
> Hvis du får en feil om at "namespace ikke eksisterer", kan du enkelt lage denne med:
> `kubectl create namespace staging`. (Det samme gjelder for Steg 2!)

## Steg 1

Første steget er selvsagt å deploye den nye versjonen til staging miljøet vårt. Åpne
`overlays/kustomization.yaml` og endre docker image tagen til den nye versjonen og redeploy appen!

**Den nye versjonen av Docker bildet har taggen _v2_**

## Steg 2

Gratulerer! Du har nå klart å deploye den nye versjonen i staging miljøet :star-eyes:.

QA testerne sier at alt ser bra ut så det er på tide å rulle appen ut i produksjon. MEN, som du ser
så manger prod konfigurasjonen til appen. Det er din jobb å legge til konfigurasjonen for prod
miljøet. Den skal oppfylle følgende:

- Prod appen skal leve i _namespacet_ `production`
- Appen skal være tilgjengelig under domenet `kube.prod`
- Den skal ha 4 replicas (kopier)
- Når du kjører appen skal det under http://kube.prod/config stå `PRODUCTION` under miljø (du har
  ikke lov til å endre noen filer under base/ mappen)

> For å deploye prod miljøet kan du bruke kommandoen `kubectl apply -k overlays/prod`
