# D-Flow Slide BatchTool
Tool voor het uitvoeren van batch-berekeningen met D-Flow Slide.

# Versies en aanpassingen
De meest recente release van de BatchTool is versie 0.11, uit 2025. Deze versie is ontwikkeld voor gebruik in combinatie met D-Flow Slide 20.1.2, die kan worden verkregen via het Informatiepunt Leefomgeving, Iplo.nl.

De voorgaande release van de BatchTool stamt uit 2019 en heeft het (helaas verwarrende) versienummer 1.0.

# Doel
Het automatisch genereren en doorrekenen van een batch D-Flow Slide berekeningen en het wegschrijven van de belangrijkste resultaten van de gedetailleerde beoordeling.

Met de BatchTool kan op snelle wijze een serie doorsnedes van een dijkvak of dijktraject worden geanalyseerd met D-Flow Slide of kan een parameterstudie met D-Flow Slide worden uitgevoerd, bijvoorbeeld om te bepalen wat het effect op de kans op zettingsvloeiing is van onzekerheden in materiaalparameters of schematisering (ligging karakteristieke punten), maar ook het effect van de ontwikkeling van de onderwater-geometrie in de tijd. 

De BatchTool kan de voor D-Flow Slide benodigde karakteristieke punten bepalen met een daarvoor ontwikkeld algoritme. De karakteristieke punten kunnen ook handmatig worden geselecteerd. 

De tool kan gebruikt worden voor een eenvoudige en gedetailleerde beoordeling volgens het BOI (global check en detailed check in de WBI-mode), niet voor de advanced models die eveneens in D-Flow Slide zitten en ook niet voor de global en detailed check in de expert-mode.

# Installatie
De BatchTool kent geen installer. De applicatie zelf kan worden gedownload via de release van deze repository. Het betreft het bestand 'D-FlowSlide_Batchtool.exe'.

# Gebruik en functionaliteit
Basis is het Excel template van waaruit de BatchTool de D-Flow Slide files genereert. In het tabblad geometry staan de XY-coördinaten van één of meerdere profielen (in D-Flow Slide is dit de surface line). Deze kunnen bijvoorbeeld uit een bestaande D-Flow Slide som gecopy-paste worden. In het tabblad materials worden de grondlagen gedefinieerd, inclusief de grondeigenschappen die specifiek zijn voor een grondlaag (dat wat in D-Flow Slide onder Tables staat). 

In het tabblad parametric study worden de scenario's ingevoerd. Per scenario één regel. In het template zijn een aantal scenario's ingevoerd. Deze kunnen worden gewijzigd en extra scenario's kunnen worden toegevoegd door het copy pasten van een regel naar een volgende regel en naar wens één of meerdere parameters aan te passen. Het aantal kolommen of koppen van de kolommen mag niet gewijzigd worden. Dat betekent dat het aantal grondlagen (layers) maximaal 10 is. In de kolommen waar soil name boven staat, moet worden aangegeven welke grondlagen in het tabblad materials geselecteerd moeten worden. In de eerste kolom (Surface Line) moet worden aangegeven welke surface line in het tabblad geometry moet worden gebruikt. Het is wel belangrijk dat de karakteristieke punten ook allemaal als XY-coördinaat in de surface line in het tabblad geometry voorkomen.

Ook in het tabblad geometry kunnen extra surface lines worden toegevoegd door de kolommen naar rechts te kopiëren en aan te passen. In het tabblad materials kunnen extra grondlagen worden toegevoegd door een regel naar onderen te kopiëren en aan te passen.
Opgemerkt wordt voor de global check en de optredingskans in de detailed check alleen de karakteristieke punten worden gebruikt in de berekening, en de surface line alleen wordt getoond in D-Flow Slide. Voor berekening van overschrijding van de kritieke inscharingslengte in de detailed check wordt ook de surface line ook daadwerkelijk in de berekening gebruikt.

In de Excel file mogen de namen van de tabbladen niet veranderd worden en ook niet de koppen van de kolommen (in materials alleen de eerste regel, in geometry en parametric study de eerste drie regels). Na het wijzigen en opslaan van de Excel file kan de BatchTool gestart worden. Hierin moet (in willekeurige volgorde) geselecteerd worden:

- de folder waarin de Excel file staat
- de folder waarin D-Flow Slide 20.1.2 staat
- de folder waarin de automatisch gegeneerde resultaten per scenario worden weggeschreven. Bij het (opnieuw ) starten van de BatchTool verschijnt bij het selecteren van de folder default de folder waarin de batch tool staat. Na selectie van de eerste folder, verschijnt bij het selecteren van de volgende folder default de eerst geselecteerde folder. Het is dus handig om de verschillende folders bij elkaar te zetten.

De BatchTool genereert de volgende resultaten:
- Twee D-Flow Slide files per scenario: één nog niet doorgerekend en (mits mogelijk) één wel doorgerekend
- Een png file met de surface line en karakteristieke punten per scenario
- Een Excel file met de toegepaste input parameters per doorgerekende doorsnede
- Vier csv files met de belangrijkste resultaten van de detailed check per batch doorgerekende doorsnedes.

Om het automatisch bepalen van de karakteristieke punten met de BatchTool goed te laten verlopen, moeten de dijkprofielen en de onderwater-geometrieën zoveel mogelijk worden ontdaan van ruis, zoals grillige dijkprofielen als gevolg van begroeiing of incomplete bathymetrie. Bij schaardijken worden de karakteristieke punten 'Dike toe at river' en 'Insert river channel' vaak niet precies gevonden, door de lange taluds zonder duidelijke knikpunten. Handmatige bijstelling kan dan nodig zijn.

# Technische informatie
De D-Flowslide BatchTool is een executable geschreven in Python. Het is een experttool. Basis is een template D-Flow Slide file, die gemanipuleerd wordt. De invoer- en uitvoerfiles hebben een Excelformaat. 
Voor gebruik van de BatchTool is D-Flow Slide benodigd; het is geen zelfstandige applicatie. Aanbevolen wordt de vigerende versie van D-Flow Slide, op moment van schrijven is dit versie 20.1.2.

# License
De code voldoet aan de volgende license: GNU GENERAL PUBLIC LICENSE, Version 3, 29 June 2007.

# Contactpersoon
Iris van de Kerk, (Iris.vande.kerk@rws.nl) Rijkswaterstaat-WVL 

Thomas van Walsem (thomas.van.walsem@rws.nl) Rijkswaterstaat-WVL
