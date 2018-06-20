# Helserefusjon - åpne data
REST API med åpne data fra Helserefusjonsområdet. APIet leverer data på JSON og XML format.  

Det tilbys API for følgende områder:
- Bandasjister med direkte oppgjørsavtale
- Takstkoder
- Labratoriekodeverk (NLK-koder)
- NLK refusjonskategorier

Lisens for offentlige data https://data.norge.no/nlod/no

Se også https://ehelse.no/takster

## Bandasjister med direkte oppgjørsavtale
URL https://helserefusjoner-kuhr.nav.no/rest/opne-data/v1/bandasjister

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
URL https://helserefusjoner-kuhr.nav.no/rest/opne-data/v1/takstkoder

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


## Labratoriekodeverk (NLK-koder)
URL https://helserefusjoner-kuhr.nav.no/rest/opne-data/v1/nlkkoder

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


## NLK refusjonskategorier
URL https://helserefusjoner-kuhr.nav.no/rest/opne-data/v1/refusjonskategorisatser

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




