Inhoudsopgave
- [Implementatie VERA in Empire](#implementatie-vera-in-empire)
  - [Algemeen](#algemeen)
  - [Authenticatie](#authenticatie)
  - [Subscription – Notification](#subscription--notification)
  - [REST](#rest)
- [Geïmplementeerde uitgaand VERA procesberichten](#geïmplementeerde-uitgaand-vera-procesberichten)
  - [Onderhoudsverzoek Synchroniseren](#onderhoudsverzoek-synchroniseren)
    - [VERA compliance](#vera-compliance)
  - [Onderhoudsorder Synchroniseren](#onderhoudsorder-synchroniseren)
  - [Opvragen afspraakopties](#opvragen-afspraakopties)
  - [Bevestigen afspraak](#bevestigen-afspraak)
- [Geïmplementeerde inkomende VERA procesberichten](#geïmplementeerde-inkomende-vera-procesberichten)
  - [Onderhoudsorder Statuswijziging Synchroniseren – ondord](#onderhoudsorder-statuswijziging-synchroniseren--ondord)
  - [Onderhoudsbesteding Synchroniseren](#onderhoudsbesteding-synchroniseren)
  - [Afspraak Synchroniseren](#afspraak-synchroniseren)
- [Geïmplementeerde VERA gegegevensberichten](#geïmplementeerde-vera-gegegevensberichten)
  - [Relatie – relmdw](#relatie--relmdw)
  - [Relatie – relnat](#relatie--relnat)
  - [Relatie – relrec](#relatie--relrec)
    - [Endpoint](#endpoint)
  - [NatuurlijkPersoon – relnat](#natuurlijkpersoon--relnat)
  - [RechtsPersoon – relrec](#rechtspersoon--relrec)
  - [Eenheid – vaseen](#eenheid--vaseen)
  - [CollectiefObject - vascol](#collectiefobject---vascol)
- [Geïmplementeerde niet-VERA types](#geïmplementeerde-niet-vera-types)
  - [Rayon](#rayon)
  - [Magazijn](#magazijn)
  - [Artikel](#artikel)
  - [Standaardtaak](#standaardtaak)
- [Entiteiten](#entiteiten)

# Implementatie VERA in Empire

## Algemeen
Dit document beschrijft de wijze waarop Empire integreert met andere softwarepartijen op basis van de VERA standaard.
Dynamics Empire is in de basis ontwikkeld in Microsoft Business Central. Integratie wordt door dit platform ondersteund in de vorm van REST API's.

## Authenticatie
Microsoft Business Central ondersteunt twee authenticatiemethoden: OAuth2 en Basic Authentication. OAuth2 alleen de grant flow voor interactieve logins. Basic authentication wordt ondersteund, maar afgeraden in productie.

## Subscription – Notification
De kennisgevingsberichten voor gegevensberichten worden in Empire beschikbaar gesteld via notifications die middels een subscription op een entiteit kunnen worden ingeregeld.

## REST
cegeka-dsa heeft gekozen om VERA te implementeren op basis van REST. Alle berichten sluiten volledig aan op het VERA model wat betreft de entiteitstructuur, maar ook wat betreft de referentiedata en de gegevens- en procesberichten. Enkel de technische verpakking is getransformeerd naar een REST equivalent. De reden hiervoor is dat de softwaretools zich ontwikkeld hebben naar REST en dit reeds jaren de eerste keuze is voor API’s en integraties. Deze constatering is dus niet specifiek cegeka-dsa, maar ook alle partners waarmee geïntegreerd wordt, die moderne softwaretools gebruiken. Voor die gevallen waar de partner vasthoudt aan SOAP, is een eenvoudige transformatie mogelijk, omdat er alleen een technische mapping plaats hoeft te vinden.
 

# Geïmplementeerde uitgaand VERA procesberichten

## Onderhoudsverzoek Synchroniseren

### VERA compliance
| Veldnaam | | | |

## Onderhoudsorder Synchroniseren

## Opvragen afspraakopties

## Bevestigen afspraak



# Geïmplementeerde inkomende VERA procesberichten

## Onderhoudsorder Statuswijziging Synchroniseren – ondord

## Onderhoudsbesteding Synchroniseren
De bestedingen van de servicemedewerker moeten in Empire worden geregistreerd.

## Afspraak Synchroniseren
Door het plansysteem kunnen ook afspraken gemaakt worden, die aan Empire gemeld moeten kunnen worden.



# Geïmplementeerde VERA gegegevensberichten

## Relatie – relmdw
Een variant is het vraagbericht voor planbare medewerkers -> relmdw

## Relatie – relnat
Dit bericht is afwijkend tov. de definitie in VERA. De adressen en rollen verwijzen niet naar collecties van kerngegevens, maar naar collecties van basisgegevens zodat niet voor ieder adres en iedere rol een nieuw request gedaan hoeft te worden voor adres en rol.

Ook afwijkend zijn de volgende rollen die niet bestaan in de referentiedata van VERA: inspecteur (INS), technische dienst (TED).

Het is ook mogelijk om alleen de natuurlijke personen op te vragen die planbaar zijn voor het maken van inspecties of uitvoeren van onderhoud. Dit is een filter op dit endpoint of een nieuw endpoint, afhankelijk van de mogelijkheden in BC.

Scenario: natuurlijkpersoon wordt toegevoegd aan de lijst van inspecteurs. Dit zorgt voor een notificatie van een wijziging van de natuurlijkpersoon in kwestie. De rol inspecteur zal toegevoegd zijn in de lijst van rollen.


## Relatie – relrec
Dit bericht is afwijkend tov. de definitie in VERA. De adressen en rollen verwijzen niet naar collecties van kerngegevens, maar naar collecties van basisgegevens zodat niet voor ieder adres en iedere rol een nieuw request gedaan hoeft te worden voor adres en rol.

Het is ook mogelijk om alleen de rechtspersonen op te vragen die planbaar zijn voor het maken van inspecties of uitvoeren van onderhoud. Dit is een filter op dit endpoint of een nieuw endpoint, afhankelijk van de mogelijkheden in BC.

### Endpoint
{{baseurl}}\relatie

## NatuurlijkPersoon – relnat
{{baseurl}}\natuurlijkpersoon

## RechtsPersoon – relrec
{{baseurl}}\rechtspersoon

## Eenheid – vaseen
{{baseurl}}\eenheid

## CollectiefObject - vascol
{{baseurl}}\collectiefobject


# Geïmplementeerde niet-VERA types

## Rayon

## Magazijn

## Artikel

## Standaardtaak




# Entiteiten
