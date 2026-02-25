# Kandidatoppgave

Kandidatoppgaven viser at du kan sette opp et system for overvåkning av applikasjoner og 
løsningen vil bli brukt som utgangspunkt i neste intervju. 

Ting som er relevante å vise frem:
- Finne frem i kode for å finner porter, endepunkter og eventuelt endre på disse parameterene. 
- Containerization av koden/filene. 
- IaC
- Deploy som microservices

**Vis hvordan du tenker å håndtere flere deler i et cluster. Bruk gjerne Helm charts for eksempel. Vis/beskriv hva som er viktig å tenke på i forhold til robusthet, skalering, sikkerhet, m.m.**

## Tidsbruk

En effektiv gjennomgang av oppgaven tar ca 4 timer. 

En grundig besvarelse vil ta en del lenger tid. Det er derfor lurt å lese gjennom oppgaven først og velge vekk noe hvis det er mye ukjent. 

Delene er også relativt uavhengige så det er fritt frem å hoppe over steg hvis man sitter fast. 

## Forslag til løst oppgave

**Se i `oppgavepakke` mappen først. Der er det hjelp til å komme i gang med et grunnleggende oppsett.**

Klienten sender en forespørsler til server, og mange av dem er misslykket. 

Serveren tar imot json med beskrivelse av dyr hvor det er en del krav. Hester og hunder
trenger å ha 4 bein. Noen dyr tar lengre tid, og noen kan lage feil.

Under er et forslag til steg for løsning. Det vil være forskjellig erfaringsnivå på kandidater og derfor må du se selv hvordan det er fornuftig å bruke tiden. 

*Husk å legge ved screenshots i besvarelsen*.

Hvis du har god kontroll på oppgaven så er det positivt om du legger til flere elementer.

Husk at alle hjelpemidler, bortsett fra å få hjelp av andre personer, er tilgjengelig. ChatGPT er behjelpelig for mye av dette, samt Grafana blogger og forum m.m.

**Lever besvarelsen på GitHub.** Legg ved Dockerfiler, yaml filer, eller hva enn du velger å bruke for å løse oppgaven.
Legg også ved en **README.md** som beskriver løsningen og kjøring av systemet. 
**Lever oppgaven som et privat repo som du deler med brukerene spesifisert i innkallingen.**

### Container

Sett opp et kubernetes cluster lokalt med f.eks. kind eller minikube.

Kjør server og klient som seperate pods. Gjennomfør resten av oppgaven i cluster. Nye komponenter som legges til bør leve i clusteret.

Husk å endre `SERVER_URL` i client koden.

( Hvis du får problemer med å lage containers av koden, så kan du prøve å finne alternativer som viser kommunikasjon mellom pods/containers )


### Grafana

Legg til Grafana og sjekk at den kjører. Siste versjon burde fungere fint for denne oppgaven. 

Det er best om du får med metrikker og logg fra server/client, men om du ikke får til den delen så finnes det standard metrikker.

### Metrikker

Legg til Prometheus og scrape metrikker. 

DataSource for Prometheus må settes opp i Grafana.

Se at metrikkene er tilgjengelige i Grafana med å bruke riktig DataSource.

(Hvis du ikke får data i Grafana så er det lurt å sjekke Prometehus direkte først for å se om data er tilgjengelig der.)


### Logger

Legg til Loki som komponent. 

**En utfordring her er å bruke microservice mode**

Bruk Promtail for å sende loggene. 

Se at loggene er tilgjengelig i Grafana fra Loki. Husk å sette opp DataSource for Loki og å ta den i bruk i Grafana.

OBS: Loggene er enkle og har ikke mye å sortere på. Det er ikke forventet at det finnes gode labels annet enn å sortere på hvilken komponent det gjelder.

## Ekstra

Oppgaver som kan gjøres om det blir nok tid. 

### CI/CD

Sett opp en pipeline i Github eller liknende hvor du viser at du forstår hvilke steg 
som er relevante. 

Du kan også legge dette til lokalt med Jenkins om du er konfortabel med det.

### Skalering i cluster

Kan antall podder bli satt automatisk?

