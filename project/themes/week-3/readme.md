<p align="center">
    <img width="250px" src="../../../images/theme-3.png"/>
</p>

# Nedbrydning: Svamperiget (Tema 3)

- [Description](#description)
- [Included input files](#included-input-files)
- [Requirements overview](#requirements-overview)
- [Recommended approach](#recommended-approach)
- [Corrections from the biologist](#corrections-from-the-biologist)

This document contains a description of the third theme of the project.
This document is structured so that:
- **description** gives an insight into what our "mini-world" should be able to support when the theme is completed.
- **Included input files** shows the files the program should be able to load when the theme is completed.
- **Requirements** overview gives an overview of various requirements that need to be supported.
- **Recommended approach** breaks down various requirements and suggests how you can approach the theme from start to finish.

# Description
Naturen har forskellige faser. En vigtig, men typisk overset del af dette, er nedbrydning. Nedbryderne er dem som hjælper med at gøde naturen, og meget mere. Her kan vi klart anbefale dokumentaren Fantastic Fungi eller episode to af dokumentarserien ’den blå planet’. Det er denne del af nature, der sørger for at det hele løber rundt! Og netop dette er fokus for denne uge. Måske vi også møder dele af dyreriget som på det sidste har vundet stort indpas gennem spil og tv-serier?

# Included input files
```
t3-1a.txt
t3-1b.txt
t3-1c.txt
t3-2ab.txt
tf3-1a.txt
tf3-2a.txt
tf3-3ab.txt
```

Note omkring input filer: Selvom denne uge primært består i at tilføje ting som ’tilfældigt’ kan opstå på kortet, bliver disse også indlæst fra filer. De indlæses ligesom dyr tidligere har været gjort, med undtagelse af Cordyceps svampen, hvor der også angives hvilket dyr det skal knyttes til:
 
```
N
carcass 1
carcass fungi 1-10
cordyceps rabbit 1
cordyceps wolf 1-5
```

# Requirements overview
Når følgende krav er opfyldt, er tema 3 gennemført. Ligesom i sidste uges temabeskrivelse, har alle krav og input filer har et ID for at hjælpe på vej. De enkelte krav denne uge er større end tidligere, til gengæld er der færre. Udover de obligatoriske krav, følger frivillige krav nederst i kravoversigten.

-	**K3-1a**. Opret ådsler, som placeres på kortet når input filerne beskriver dette.
-	**K3-1b**. Når dyr dør nu, skal de efterlade et ådsel. Ådsler kan spises ligesom dyr kunne tidligere, dog afhænger mængden af ’kød’ af hvor stort dyret der døde er. Således spises dyr ikke direkte længere når det slås ihjel, i stedet spises ådslet. Alle dyr som er kødædende spiser ådsler.
-	**K3-1c**. Ådsler bliver dårligere med tiden og nedbrydes helt – selvom det ikke er spist op (altså forsvinder det)! Det forsvinder naturligvis også hvis det hele er spist.
-	**K3-2a**. Udover at ådsler nedbrydes, så hjælper svampene til **[1]**. Således kan der opstå svampe I et ådsel **[2]**. Dette kan ikke ses på selve kortet, men svampen lever I selve ådslet. Når ådslet er nedbrudt (og forsvinder), kan den ses som en svamp placeret på kortet, der hvor ådslet lå **[3]**. For at læse inputfilerne skal du sikre dig, at et ådsel kan indlæses med svamp.
-	**K3-2b**. Svampe kan kun overleve, hvis der er andre ådsler den kan sprede sig til i nærheden. Er dette ikke tilfældet, vil svampen også dø efter lidt tid. Desto større ådslet er, desto længere vil svampen leve efter ådslet er væk. Da svampen kan udsende sporer, kan den række lidt længere end kun de omkringliggende pladser.


## Frivillige, ikke obligatoriske, krav.

-	**KF3-1a**. Når en svamp dør, er jorden ekstra gunstig. Derfor opstår græs på sådanne felter, når svampen dør **[4]**.
-	**KF3-2a**. Ikke alle typer svampe lever på døde dyr. Der eksisterer også en anden type svamp (Cordyceps) **[5]**. Denne svamp spreder sig til, og styrer, (kun) levende dyr. Deres livscyklus er den samme som de tidligere svampe; de nedbryder langsomt dyret, og er der ikke mere tilbage af dyret, dør svampen snart efter. Når svampen har tæret nok på dyret, dør dyret. Da denne svamp nedbryder dyret mens det lever, er der ikke noget ådsel efter døden. Svampen dør også når dyret dør, med undtagelsen af krav 
-	**KF3-3a**.  Når Cordyceps’ vært dør, forsøger den at sprede sig til levende dyr i nærheden, og kun på dette tidspunkt. Igen kan denne svamp sprede sig lidt længere end de omkringliggende pladser da den sender sporer ud.
- **KF3-3b**. Når et dyr er inficeret med Cordyceps svampen, overtager svampen dyrets handlinger. Dyret gør derfor som svampen bestemmer, hvilket er at søge mod andre dyr af samme art. 

# Recommended approach
Det anbefales at denne uge også starter med en objekt-orienteret analyse ved at kigge på teksten, input filernes indhold, samt de forskellige krav. Således står I med et overblik over hvad der skal tilføjes. 

Denne gang kan det være svært at se, om der er mulighed for at genbruge eksisterende kode. I kommer dog med sikkerhed til at skulle modificere tidligere kode, og deraf opstår der muligheder for at tilføje yderligere abstraktioner. F.eks., da alle dyr kan overtages af den samme svamp, bør der ske en refaktorisering der sørger for at vi kan genbruge koden omkring denne nye opførsel. Overvejelserne omkring dette gør sig også godt i ugens dagbog. Husk at overvej hvordan dette påvirker tidligere tests, og opdatér dem som nødvendigt. 

Synes man det er svært at begynde på implementationen af svampe, kan man med fordel starte med at tænke på, at svampe ikke anvende Actor interfacet før de placeres i verdenen og indtil da, agerer ved kald fra det dyr de har inficeret. Der er dog flere måder at implementere dette på. 

Inden I går i gang med at programmere, vil vi blot nævne, at denne uge også har flere ’usynlige’ elementer der ikke (altid) kan ses på kortet. Her kan man med fordel kigge mod DynamicDisplayInformationProvider som tillader at skifte udseende på et element under eksekveringen. Dette kan specielt være en fordel med de her svampe da de ikke nødvendigvis eksisterer på kortet selv. Har I ikke brugt interfacet før, vil I nok finde det interessant eventuelt også at bruge det for tidligere dyr I har implementeret. Dertil er unit tests særdeles vigtigt denne uge, da det kan være svært, at vurdere hvorvidt programmet opfører sig som forventet.

Det kan være du efterfølgende skal undersøge yderligere hvad der er tilgængeligt i World klassen. Måske er der ting I ikke brugte sidste uge, som kunne være gode at anvende denne uge.



# Corrections from the biologist

**[1]** F.eks. svampe af slægten Mucor

**[2]** Normalt ser man ikke så ofte direkte svamp i nedbrydningen, da nedbrydningen af ådsler oftest bliver udført af insekter og bakterier. Svampe er til gengæld utroligt gode til at nedbryde planter osv. F.eks. bliver ens kødpålæg ofte råddent (pga. bakterier) hvorimod ens brød og frugt bliver angrebet af svamp (Mug).

**[3]** Når ådslet er nedbrudt vil svampene dø da deres vækstgrundlag er væk. Her er det svampens mission at nå at sprede sig til et nyt substrat inden ådslet er væk. Derudover er det en stor proces at nedbryde et lig, og flere arter af svampe udfylder forskellige stadier af nedbrydningen, det samme gælder for de bakterier og smådyr der også er en del af processen. Se eksempelvist, artiklen her.

**[4]** Hekseringe er et sjovt eksempel på svampes effekt på græsvækst, se eksempelvis her.

**[5]** Typen kaldes entomophatogenic fungi, og der findes 1000+ arter fordelt på flere familier og ordener af svampe. Det er også i naturen kun insekter / leddyr der bliver ramt af disse. Så havde det været naturligt, så ville vores bjørne/ulve/kaniner være i sikkerhed.


