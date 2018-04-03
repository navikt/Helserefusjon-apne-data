# Helserefusjon - åpne data
REST API med åpne data fra Helserefusjonsområdet. APIet leverer data på JSON format.  

Lisens for åpne data https://data.norge.no/nlod/no/

## Bandasjister og direkte oppgjørsavtaler
URL https://tjenester.nav.no/helserefusjon/rest/bandasjister

### Data innhold
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
tidspunkt_oppdatert |Når bandasjisten siste ble oppdater i SAR 