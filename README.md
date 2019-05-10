# Helserefusjon - åpne data
HTTP API med åpne data fra Helserefusjonsområdet. APIet leverer data på JSON og XML format.  

Det tilbys API for følgende områder:
- Aggregert takstbruk
- Bandasjister med direkte oppgjørsavtale
- Takstkoder
- Labratoriekodeverk (NLK-koder)
- NLK refusjonskategorier


Lisens for offentlige data https://data.norge.no/nlod/no

Se også https://ehelse.no/takster


## Aggregert takstbruk
APIet tilbyr takstbruk statistikk for kommuner og fylker, fordelt på år, måned, fagområder og praksistyper. Den geografiske inndeling
er basert på behandlers adresse. For kommuner/år er tallene begrenset til å bare ta med takster der antallet er større enn 5. For kommune/måned tallene
er det begrenset til kommuner over 10 000 innbyggere. 

### Datainnhold
Felt | Beskrivelse
-----|------------
ar |
maned |
takstkode |
fagomraade |
praksis_type_kode |
behandler_kommunenr |
behandler_fylke |
antall_regninger |
sum_refusjon |
sum_egenandel_betalt_av_pasient |
sum_egenandel_dekket_av_folketrygden |

### API

#### Kommune / Måned
Parameter | Beskrivelse
-----|------------
HTTP Header: Accept| Angir hvilket format data skal leveres på. Støtter application/xml og application/json
Query: fagomraade | Obligatorisk, komma separerte verdier. Se kodeverk for mulig verdier
Query: fommaned | Obligatorisk, lengden på perioden kan ikke være mer enn 13 måneder
Query: tommaned | Obligatorisk, lengden på perioden kan ikke være mer enn 13 måneder
Query: takstkoder | Komma separerte verdier. Se kodeverk for mulig verdier
Query: kommuner | Komma separerte verdier. Se kodeverk for mulig verdier
Query: praksistyper | Komma separerte verdier. Se kodeverk for mulig verdier

##### Eksempel:
https://helserefusjoner-kuhr.nav.no/api/opne-data/v1/takstbruk/agtakst/kommune/maned?fagomraade=LE&fommaned=201805&tommaned=201905&takstkoder=H1&kommuner=0301&praksistyper=FALE,LEVA

#### Kommune / År

Parameter | Beskrivelse
-----|------------
HTTP Header: Accept| Angir hvilket format data skal leveres på. Støtter application/xml og application/json
Query: fagomraade | Obligatorisk, komma separerte verdier. Se kodeverk for mulig verdier
Query: fomar | Obligatorisk
Query: tomar | Obligatorisk
Query: takstkoder | Komma separerte verdier. Se kodeverk for mulig verdier
Query: kommuner | Komma separerte verdier. Se kodeverk for mulig verdier
Query: praksistyper | Komma separerte verdier. Se kodeverk for mulig verdier

##### Eksempel:
https://helserefusjoner-kuhr.nav.no/api/opne-data/v1/takstbruk/agtakst/kommune/ar?fagomraade=LE&fomar=2015&tomar=2019&takstkoder=H1&kommuner=0301&praksistyper=FALE,LEVA

#### Fylke / Måned

Parameter | Beskrivelse
-----|------------
HTTP Header: Accept| Angir hvilket format data skal leveres på. Støtter application/xml og application/json
Query: fagomraade | Obligatorisk, komma separerte verdier. Se kodeverk for mulig verdier
Query: fommaned | Obligatorisk, lengden på perioden kan ikke være mer enn 13 måneder
Query: tommaned | Obligatorisk, lengden på perioden kan ikke være mer enn 13 måneder
Query: takstkoder | Komma separerte verdier. Se kodeverk for mulig verdier
Query: fylker | Komma separerte verdier. Se kodeverk for mulig verdier
Query: praksistyper | Komma separerte verdier. Se kodeverk for mulig verdier

##### Eksempel:
https://helserefusjoner-kuhr.nav.no/api/opne-data/v1/takstbruk/agtakst/fylke/maned?fagomraade=LE&fommaned=201805&tommaned=201905&takstkoder=H1&fylker=03,15&praksistyper=FALE,LEVA

#### Fylke / År

Parameter | Beskrivelse
-----|------------
HTTP Header: Accept| Angir hvilket format data skal leveres på. Støtter application/xml og application/json
Query: fagomraade | Obligatorisk, komma separerte verdier. Se kodeverk for mulig verdier
Query: fomar | Obligatorisk
Query: tomar | Obligatorisk
Query: takstkoder | Komma separerte verdier. Se kodeverk for mulig verdier
Query: fylker | Komma separerte verdier. Se kodeverk for mulig verdier
Query: praksistyper | Komma separerte verdier. Se kodeverk for mulig verdier

##### Eksempel:
https://helserefusjoner-kuhr.nav.no/api/opne-data/v1/takstbruk/agtakst/fylke/ar?fagomraade=LE&fomar=2015&tomar=2019&takstkoder=H1&fylker=03,15&praksistyper=FALE,LEVA

#### Hele landet / måned

Parameter | Beskrivelse
-----|------------
HTTP Header: Accept| Angir hvilket format data skal leveres på. Støtter application/xml og application/json
Query: fagomraade | Obligatorisk, komma separerte verdier. Se kodeverk for mulig verdier
Query: fommaned | Obligatorisk, lengden på perioden kan ikke være mer enn 13 måneder
Query: tommaned | Obligatorisk, lengden på perioden kan ikke være mer enn 13 måneder
Query: takstkoder | Komma separerte verdier. Se kodeverk for mulig verdier
Query: praksistyper | Komma separerte verdier. Se kodeverk for mulig verdier

##### Eksempel:
https://helserefusjoner-kuhr.nav.no/api/opne-data/v1/takstbruk/agtakst/landet/maned?fagomraade=LE&fommaned=201805&tommaned=201905&takstkoder=H1&praksistyper=FALE,LEVA

#### Hele landet / år

Parameter | Beskrivelse
-----|------------
HTTP Header: Accept| Angir hvilket format data skal leveres på. Støtter application/xml og application/json
Query: fagomraade | Obligatorisk, komma separerte verdier. Se kodeverk for mulig verdier
Query: fomar | Obligatorisk
Query: tomar | Obligatorisk
Query: takstkoder | Komma separerte verdier. Se kodeverk for mulig verdier
Query: praksistyper | Komma separerte verdier. Se kodeverk for mulig verdier

##### Eksempel:
https://helserefusjoner-kuhr.nav.no/api/opne-data/v1/takstbruk/agtakst/landet/ar?fagomraade=LE&fomar=2015&tomar=2019&takstkoder=H11&praksistyper=FALE,LEVA


## Bandasjister med direkte oppgjørsavtale
URL https://helserefusjoner-kuhr.nav.no/api/opne-data/v1/bandasjister

Henter ut siste gjeldende oversikt over bandasjister som er registrert med direkte oppgjørsavtale i Helfos Samhandlerregister (SAR).

### Datainnhold
Felt | Beskrivelse
-----|------------
sar_id |Unik id for samhandleren i SAR 
sar_navn |Navn på bandasjist lagret i SAR 
sar_orgnr |Orgnr. bandasjisten er lagret med i SAR og det er inngått avtale på 
hovedenhet_orgnr |Bandasjistens hovedenhet hentet fra BRREG. Kan være det samme som sar_orgnr
underenhet_orgnr |Bandasjistens underenhet hentet fra BBREG. Kan være det samme som sar_orgnr. Vil ikke finnes hvis bandasjisten er registrert i SAR med hovedenhetens orgnr.
gyldig_fra |Fra og til dato for når bandasjisten er gyldig. Styres av avtale og praksis registrering gjort i SAR av Helfo. 
gyldig_til | 
status |Kan ha verdien "slettet" hvis bandasjisten ikke lenger er en aktiv enhet i BRREG.
tidspunkt_registrert |Når bandasjisten ble registrert i SAR 
tidspunkt_oppdatert |Når bandasjisten sist ble oppdatert i SAR 

### Parametre
Parameter | Beskrivelse
-----|------------
HTTP Header: Accept| Angir hvilket format data skal leveres på. Støtter application/xml og application/json

## Takstkoder
URL https://helserefusjoner-kuhr.nav.no/api/opne-data/v1/takstkoder

### Datainnhold
Felt | Beskrivelse
-----|------------
takst_id |
takstkode |
fagomraade |
fradato |
tildato |
honorar |
refusjon |
egenandel |
pasient_egenbetaling |
maks_repetisjoner |
repetisjonsprosent |
redusert_ref_fra_repetisjon |
redusert_repetisjonsprosent |
spesialisttakst |
ugyldig_kombinasjon |
krever_takst |
krever_prosedyre |
krever_diagnose |
maks_antall_per_aar |
maks_antall_per_kalender_aar |
maks_antall_gjelder_pasient |
minimum_tidsbruk |
beskrivelse |


### Parametre
Parameter | Beskrivelse
-----|------------
HTTP Header: Accept| Angir hvilket format data skal leveres på. Støtter application/xml og application/json
Query: fagomraade | AP - Audiopedagog, BE - Behandlingsreiser i utlandet, FBV - Fritt behandlingsvalg, FY - Fysioterapi, HS - Helsestasjon, JO - Jordmor, KI - Kiropraktor, LE - Lege, LOGO - Logoped, LR - Privat lab/radiologi, OR - Ortoptist, PO - Poliklinikk, PS - Psykolog, PT - Primærhelseteam, RE - Rehabiliteringsinstitusjon, TH - Tannhelse, TP - Tannpleier
Query: gyldigdato | Filtrerer takstene til kun de som er gyldig på en gitt dato. Dato på formatet  yyyy-MM-dd
Query: takstkode | Filtrer takstene til en gitt kode, kan kombineres med de andre parametrene eller brukes alene.
Query: beskrivelse | Filtrer på beskrivelsen til takstkoden, kan kombineres med de andre parametrene eller brukes alene.

For query på takstkode og beskrivelse kan %25 brukes for å angi wildcard søk. Feks. %25undersøkelse%25 for å søke på alt som inneholder undersøkelse.

#### Eksempel:
https://helserefusjoner-kuhr.nav.no/api/opne-data/v1/takstkoder?gyldigdato=2018-08-09&takstkode=2ad


## Labratoriekodeverk (NLK-koder)
URL https://helserefusjoner-kuhr.nav.no/api/opne-data/v1/nlkkoder

### Datainnhold
Felt | Beskrivelse
-----|------------
nlkKodeid |
nlkKode |
norsk_bruksnavn |
komponent |
system |
enhet |
egenskapsart |
spesifisertKomponent |
npuDefinisjon |
npuSpesialitet |
fagomraadeSekundaert |
fagomraadeNlk |
fradato |
tildato |
refusjonskategori |
erstattesAv |
hvaEndret |
sistEndretDato |
stjernekode |
ugyldigKombinasjon |
refusjonskategorisats | Liste av refusjonskategorier, se NLK refusjonskategorier for beskrivelse av feltene.


### Parametre
Parameter | Beskrivelse
-----|------------
HTTP Header: Accept| Angir hvilket format data skal leveres på. Støtter application/xml og application/json
Query: gyldigdato | Filtrerer kodene til kun de som er gyldig på en gitt dato. Dato på formatet  yyyy-MM-dd
Query: nlkkode | Filtrer til en gitt kode
Query: samhandlertype | PO - Poliklinikk, LR - Privat lab/radiologi

For query på nlkkode %25 brukes for å angi wildcard søk.

#### Eksempel:
https://helserefusjoner-kuhr.nav.no/api/opne-data/v1/nlkkoder?gyldigdato=2018-08-09&samhandlertype=PO

## NLK refusjonskategorier
URL https://helserefusjoner-kuhr.nav.no/api/opne-data/v1/refusjonskategorisatser

### Datainnhold
Felt | Beskrivelse
-----|------------
refusjonskategoriid |
refusjonskategori |
refusjonssats |
fradato |
tildato |


### Parametre
Parameter | Beskrivelse
-----|------------
HTTP Header: Accept| Angir hvilket format data skal leveres på. Støtter application/xml og application/json
Query: gyldigdato | Filtrerer kodene til kun de som er gyldig på en gitt dato. Dato på formatet  yyyy-MM-dd
Query: samhandlertype | PO - Poliklinikk, LR - Privat lab/radiologi

#### Eksempel:
https://helserefusjoner-kuhr.nav.no/api/opne-data/v1/refusjonskategorisatser?gyldigdato=2018-08-09&samhandlertype=PO




