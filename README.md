Kwaliteitscontrole data
===========
**Aanspreekpunt**
Paul Bos – Root B.V.

**Samenvatting**
Controle van de kwaliteit van BIM data. Momenteel zijn de voorbeelden vooral gebaseerd op gebruik van Solibri. Aanvullingen zijn welkom. 

**Doelgroep**
Met name projectmanagers, maar ook modelleurs.

Deze pagina is een weergave van de open source ontwikkelomgeving op [github](https://github.com/BIM-Handboek-NL/BIM-kwaliteitscontrole). U kunt een bijdrage leveren door een 'pull request'  te sturen op github, of het aanspreekpunt van deze pagina te benaderen via e-mail. 

-----------

###Uitgangspunten
•	Controle op basis van IFC-modellen
•	IFC modelcheckers / IFC modelviewers

###Drie Niveaus van controle
Kwaliteitscontrole kan via verschillende richtingen ingestoken worden. 
1.	**Monodisciplinair**:  de kwaliteit van een disciplinemodel (waarin bijvoorbeeld, ontbrekende elementen, afwijkingen mbt programma van eisen, wet en regelgeving etc.)
2.	**Multidisciplinair**:  ook wel onderlinge coördinatie genoemd (clashes tussen installatie en constructieve elementen)
3.	**Discipline-overstijgend**: informatie in een BIM-model wordt hergebruikt t.b.v. beheer, calculatie etc.
Voor de verschillende doeleinden controleer je op verschillende zaken, maar waar moet je op letten, en hoe controleer je dit? 

###Vereisten aan een IFC model
**Monodisciplinair**: 
Een toets op dit niveau is volledig afhankelijk van de doelstelling. Vaak gaat het echter om de herkenbaarheid van objecten (de regelset moet bijvoorbeeld weten wat een vluchtdeur is als deze een vluchtroute-analyse moet uitvoeren). 

**Multidisciplinair**: 
1.	Gebruik de juiste exportinstellingen waardoor in het ifc-model de objecten met de juiste entiteit worden gerepresenteerd (balk met *IfcBeam*, kolom met *IfcColumn* etc). Voor alle ifc entiteiten en hun beschrijving kijk op: 
http://www.buildingsmart-tech.org/ifc/IFC2x3/TC1/html/index.htm
2.	Stem het nulpunt af (zie [beschrijving nationaal BIM handboek nulpunt coördinatie](http://nationaalbimhandboek.nl/onderwerpen/opzetten-van-nulpunt/))
3.	Gebruik een standaard codering om de controleregels de objecten te laten herkennen(bijvoorbeeld NL-SfB, of STABU-elementen)
Voorbeeld: om bijvoorbeeld alle prefab casco wanden te kunnen controleren met die van de prefab leverancier moet de controleregel deze wanden in een keer kunnen herkennen. Hiervoor is de NL-SfB codering 2?.2* (21.22 en 22.22) in combinatie met de materiaalnaam ‘ beton prefab’ goed genoeg. Deze vertaaltabel die de combinatie ‘ beton prefab’ en ‘ 2?.2* ‘ maakt een classificatie zoals hieronder in de afbeelding weergegeven. 

![filtering](https://raw.githubusercontent.com/BIM-Handboek-NL/BIM-kwaliteitscontrole/master/afbeeldingen/filtering.png)

 
**Discipline-overstijgend**: 
Ook dit is volledig afhankelijk van de doelstelling, maar is vaak een combinatie van ‘ monodisciplinair’  en ‘ multidisciplinair’.  Overleg met de eindgebruiker welke eisen aan het model gesteld worden.

###Codering / Filtering
De huidige standaard is het gebruik van de NL-SfB codering voor bouwkundige en constructieve elementen. Voor Installatietechnische elementen is de STABU-elementen codering het meest gebruikt. Met behulp van deze coderingen kun je snel objecten isoleren, en controleren in behapbare partjes.

Binnen Solibri Model checker is ‘*classificatie*’ de benaming voor de codering van objecten. Met Solibri model checker kun je zelf classificaties aanmaken, en met viewer kun je de codering zoals aangegeven in de modelleerapplicatie bekijken. 

    Tip: open na het exporteren van een IFC bestand dit extract met behulp van een viewer (bijvoorbeeld Solibri) om de codering snel te controleren. Hier is geen checker voor nodig, maar geeft je wel controle over het resultaat.

![Classification](https://raw.githubusercontent.com/BIM-Handboek-NL/BIM-kwaliteitscontrole/master/afbeeldingen/classificatie.png)

**Controleer op de volgende manieren deze coderingen in het IFC-model**:
1. Objectnamen: Maak hiervoor een classificatie zoals onderstaand aan om snel een groot overzicht te creëren. Een ‘*Information TakeOff*’ werkt ook goed.
![Naamgeving codering](https://raw.githubusercontent.com/BIM-Handboek-NL/BIM-kwaliteitscontrole/master/afbeeldingen/naamgeving_codering.png)

2. Classificatie (bijvoorbeeld NL-SfB). Maak een vertaaltabel aan naar een leesbare codering om snel visueel te controleren of het correct gecodeerd is. 
![Classificatie 2](https://raw.githubusercontent.com/BIM-Handboek-NL/BIM-kwaliteitscontrole/master/afbeeldingen/classificatie2.png)

3. Eigenlijk gebruik van objecten: controleer op deze manier snel of de juiste ifc-entiteit gebruikt is.
![IFC Entiteit](https://raw.githubusercontent.com/BIM-Handboek-NL/BIM-kwaliteitscontrole/master/afbeeldingen/ifcentiteit.png)

###Regelsets
Is bovenstaande allemaal gelukt? Dan ben je nu klaar om op een betrouwbare manier regelsets te gebruiken (natuurlijk kun je ook regelsets maken die een deel van bovenstaande automatisch controleren).
 

    Tip: baseer regelsets op een standaard codering. Zo hoef je niet voor elk project een nieuwe regelset aan te maken. Maak ook een vertaaltabel van code naar naamgeving. Dit is stukken minder foutgevoelig in het controlren.





