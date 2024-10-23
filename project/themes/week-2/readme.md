<p align="center">
    <img width="250px" src="../../../images/theme-2.png"/>
</p>

# Fødekæder: Prædatorer, flokdyr, og territorier (Tema 2)

- [Description](#description)
- [Included input files](#included-input-files)
- [Requirements overview](#requirements-overview)
- [Recommended approach](#recommended-approach)
- [Corrections from the biologist](#corrections-from-the-biologist)

This document contains a description of the second theme of the project.
This document is structured so that:
- **description** gives an insight into what our "mini-world" should be able to support when the theme is completed.
- **Included input files** shows the files the program should be able to load when the theme is completed.
- **Requirements** overview gives an overview of various requirements that need to be supported.
- **Recommended approach** breaks down various requirements and suggests how you can approach the theme from start to finish.

# Description
Naturen bliver denne uge endnu vildere – og mindre idyllisk. Med tilføjelsen af ulve og bjørne har de små kaniner pludseligt to naturlige fjender **[1]**. Det skaber naturligvis en usikkerhed for de små kaniner, men grundet både bjørne og ulves territorielle instinkter, jager og kæmper disse også mod hinanden **[2]**, og andre af deres egen art. Vores lille verden har udviklet sig til en sand kamp om overlevelse; fastholder bjørnene deres territorier? hvilke ulveflokke overlever? Hvilke grupper forgår? 

# Included input files
```
t2-1ab.txt
t2-1c.txt
t2-2a.txt
t2-3a.txt
t2-4a.txt
t2-4b.txt
t2-5a.txt
t2-6a.txt
t2-7a.txt
tf2-1.txt
tf2-2.txt
```

Note omkring bjørne i inputfilen: Når bjørne bliver nævnt i inputfilen har de udover de attributter nævnt i uge 1 har de et (x,y) koordinat som angiver centrummet af deres territorium, når det undlades, skal der blot vælges et tilfældigt koordinat (Dette er typisk hvis der skal tilføres flere bjørne), se følgende eksempel:

```
N
Rabbit 10
Bear 1 (3,5)  
Bear 5
```

# Requirements overview
Når følgende krav er opfyldt, er tema 2 gennemført. Ligesom i sidste uges temabeskrivelse, har alle krav og input filer har et ID for at hjælpe på vej. I denne uge er kravene ikke kategoriseret på samme måde som tema 1. Det anbefales således at du udfører en endnu mere stringent objekt-orienteret analyse til at starte med (se afsnit 4). I denne uge er kravene ikke sorteret således at det nødvendigvis giver mening at implementere de første først (nogle af disse kan være svære). Dan jer derfor et samlet overblik til at starte med. Udover de obligatoriske krav, følger frivillige krav nederst i kravoversigten.

-	**K2-1a**. Ulve kan placeres på kortet når input filerne beskriver dette.
-	**K2-1b**. Ulve kan dø, hvilket resulterer I at de fjernes fra verdenen.
-	**K2-1c**. Ulve jager andre dyr og spiser dem for at opnå energi. 
-	**K2-2a**. Ulve er et flokdyr. De søger konstant mod andre ulve i flokken. Når inputfilen beskriver (på en enkelt linje) at der skal placeres flere ulve, bør disse automatisk være i samme flok.
-	**K2-3a**. Ulve og deres flok, tilhører en ulvehule, det er også her de formerer sig. Ulve ’bygger’ selv deres huler. Møder en ulv en ulv fra en anden flok, kæmper de mod hinanden. 
-	**K2-4a**. Bjørne kan placeres på kortet når input filerne beskriver dette. 
-	**K2-4b**. Bjørne jager ligesom ulve, og spiser også alt **[3]**. 
-	**K2-5a**. Bjørnen er meget territoriel, og har som udgangspunkt ikke et bestemt sted den ’bor’. Den knytter sig derimod til et bestemt område og bevæger sig sjældent ud herfra. Dette territories centrum bestemmes ud fra bjørnens startplacering på kortet.
-	**K2-6a**. Dertil spiser bjørne også bær fra buske (såsom blåbær og hindbær) når de gror i området. Bær er en god ekstra form for næring for bjørnen (om end det ikke giver samme mængde energi som når de spiser kød), men som det er med buske går der tid før bær gror tilbage. 


## Frivillige, ikke obligatoriske, krav.

-	**KF2-1**. Hvis den ene ulv bliver voldsomt såret, underkaster den sig den sejrende ulvs flok **[4]**. En såret ulv har brug for hvile før den kan fortsætte.
-	**KF2-2**. Dog er bjørnen ikke et flokdyr **[5]**, og mødes kun med andre bjørne når de skal parre sig. Bjørnen kan også dø og fjernes her fra verdenen.
-	**KF2-3**. Bjørne der ikke er klar til at parre sig, angriber andre bjørne der bevæger sig ind på deres områder. Tilsvarende angriber de andre dyr.
-	**KF2-4**. Bjørnen er naturligvis vores øverste rovdyr i denne lille fødekæde, men det hænder at en stor nok gruppe ulve kan angribe (og dræbe) en bjørn. Dette vil i praksis være hvis flere ulve af samme flok er i nærheden af en bjørn. 

# Recommended approach
Det anbefales at denne uge også startes med en objekt-orienteret analyse ved at kigge på teksten, input filernes indhold, samt de forskellige krav. Således står I med et overblik over hvad der skal tilføjes. Denne gang fremhæver vi dog at der mange muligheder for at indtænke abstrakte klasser, interfaces, og hjælpeklasser som kan tillade jer at genbruge eksisterende kode, f.eks. kunne man forestille sig, at I tidligere har implementeret kode der giver jer en placering der er tættere på et mål (når man vil bevæge sig fra A til B). Denne kode skal nok anvendes igen og kan derfor rykkes ud som en statisk funktion i en hjælpeklasse. Dertil kunne man forestille sig at de aktører der nu skal implementeres indeholder funktionalitet der er ens for alle dyr I senere vil implementere – hvordan kunne i konkret genbruge denne kode? Således er det første I bør gøre, at refaktorisere jeres kode inden i udvikler de nye tilføjelser. Overvejelserne omkring refaktoriseringen gør sig også godt i ugens dagbog. Det kan her også give mening at revurdere tidligere tests. Er der nogle der skal laves om? Skal der laves flere?

Flere af kravene er denne uge sværere at specificere hvad de præcist betyder. Det er her jeres opgave at fortolke på dem, og klargøre (i dagbogen) hvad I har fortolket og hvorfor.

Herefter kan I kaste jer ud i at refaktorisere den eksisterende kode og implementere og teste de nye dele. I kurset mener vi unit tests ligesom der er blevet undervist i. Test løbende mens der implementeres. Her kan man igen kigge mod de gode råd i projektbeskrivelsen hvis de er for uoverskuelige til at starte med. 

Det kan være du efterfølgende skal undersøge yderligere hvad der er tilgængeligt i World klassen. Måske er der ting I ikke brugte sidste uge, som kunne være gode at anvende denne uge.

# Corrections from the biologist

**[1]** i simuleringen er de naturlige fjender. Kaniner er oftest for små til det kan betale sig for noget som en bjørn at spise dem. Ræve f.eks ville være en mere "naturlig" fjende for kaniner.

**[2]** Oftest ville sådanne dyr undgå hinanden; Det kan ikke betale sig for nogen af dem at satse livet på at angribe et andet top-rovdyr. Det er derfor noget vi ’leger’.

**[3]** En biolog ville nok beskrive det som noget lidt andet en jagt, en bjørn lever typisk af 73% planter, 22% insekter, og 5% dyr (viser en undersøgelse af sort bjørn).

**[4]** Det at ulve overgår til en ny flok sker til tider i naturen. Langt oftest vil grupper primært undgå hinanden. I tilfælde hvor kamp opstår vil de "besejrede hanner" langt oftest dø hvis ikke de når at flygte. Det samme gælder for strejfende hanner.

**[5]** ved overflod af mad i perioder kan der dannes smågrupper af bjørne; ”Bears are solitary by nature, except when in family groups of mothers and cubs or in pairs during the mating season. Bears may congregate in areas of high food density, such as oak stands, berry patches, or farm fields.”


