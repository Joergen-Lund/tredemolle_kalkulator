# Tredemølle-kalkulator

En enkel nettside som regner ut hvor langt du faktisk har løpt på tredemølle.

## Bakgrunn

På mange tredemøller fortsetter beltet å gå når du står stille i pausene mellom dragene, og da blir distansen på displayet for høy. Kalkulatoren bygger økta opp av delene du faktisk løp eller gikk, og regner ut distansen selv. Tid du sto stille telles ikke med.

## Funksjoner

- **Oppvarming:** legg inn enten tid og fart, eller ferdig distanse og tid.
- **Serier med drag:**
  - Antall drag, første draglengde og fart.
  - Automatisk stigning eller fall per drag, for eksempel +0,5 km/t eller −15 sek.
  - Du kan legge til flere serier, hver med egne verdier.
  - Gang/jogg-pause mellom dragene, med egen tid og fart.
  - Valgfri seriepause med gange/jogg etter siste drag, med egen tid og fart.
- **Nedjogg:** gange først, deretter jogging (tid og fart, eller distanse og tid).
- **Oppsummering:** reell distanse, løpetid, snittfart og snitt min/km. Dessuten en fartsgraf over økta og en fordeling per del, med egen rad for gange.
- Mobil-først design med mørk og lys modus (følger enhetens innstilling).
- Alt regnes ut i nettleseren. Det finnes ingen backend, ingen avhengigheter og ingen datainnsamling.

## Slik regnes det ut

Hver del av økta er et tidsrom med en fart, og distansen er `fart × tid`.

- **Drag nummer *i* i en serie** (der *i* starter på 0):
  - Lengde = første lengde + *i* × endring i lengde.
  - Fart = første fart + *i* × endring i fart.
- **Totalt:** summen av distanse og tid for alle deler, inkludert gange.
- **Snittfart:** total distanse delt på total tid, gange inkludert. Snitt min/km er den samme farten uttrykt som tempo.
- **Distanse og tid (oppvarming/nedjogg):** farten utledes som distanse delt på tid. Lar du tiden stå tom, regnes bare distansen med, og delen holdes utenfor løpetid og snittfart.
- Hvis en synkende endring gjør tid eller fart negativ, settes verdien til 0, og du får en advarsel.

### Inndataformat

| Felt | Format | Eksempler |
| --- | --- | --- |
| Tid | `m:ss`, `h:mm:ss` eller minutter som tall | `4:30`, `1:02:03`, `4,5` (= 4 min 30 sek) |
| Fart | km/t, komma eller punktum | `13`, `14,5` |
| Endring i lengde | sekunder, med +/−-knapp | `10`, `15` |
| Endring i fart | km/t, med +/−-knapp | `0,5` |

## Begrensninger

- Økter lagres ikke. Skjemaet nullstilles når du laster siden på nytt.
- Du legger inn én fast pause-tid og -fart per serie, ikke ulike pauser for hvert drag.
- Tilt (stigning) på mølla støttes ikke.
