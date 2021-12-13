Idag skapas alla context med variabler och objekt upp när man begär datat från servern. 

Det finns ingen cache, eller revisionskoll på instanserna. 

Följande förslag (eller strategi) är ett försök att:

1. lösa problemet med revisionshantering för objekt och hierarkier av data
2. snabba upp och lösa problemet med indexering av objekt, relationer och data
3. kunna jobba med olika revisioner av noder i samma projekt. 

Grundstrategin är att template-filer vi har nu finns kvar på exakt samma sätt. Skillnaden är att vid indexering/resolve av filer sparas resultatet ner som en graf i en databas. All navigering och konsumtion av projektet/kontot sker från grafen (*den publicerade revisionen*). Alltså förvandlas mall-filerna till just mallfiler, vilka exekveras vid access, eller vid re-indexering (publicering). 

Ett exempel: 

Det finns 10 rum, exakt likadana. Det finns en lampa, ett tilluftsdon, en radiator med styrdon, en givare som mäter temperatur och tryck, samt en parameterlista för inställningar för respektive objekt i varje rum. Vi kan kalla dessa objekt *komponenter* den översta komponenten i hierarkin är en *grupp*. grupper kan finnas i grupper. 

 I ovan exempel finns fem mallfiler, där varje fil kan innehålla definitioner av och referenser till komponenter.

1. gruppen rum. 

   - fyra referenser till andra komponentfiler
   - attribut och bindningar som beskriver rummet

2. lampan 

   - attribut och bindningar som beskriver lampan

3. tillfutsdonet

   - attribut och bindingar som beskriver donet

4. radiator

   - attribut och bindinigar som beskriver radiatorn

   - komponentdefinition för styrdon
     - attribut och bindningar som beskriver styrdonet

5. givaren

Vid publicering av varje rum genereras instanser utifrån mall-filerna. instanserna har inte längre några makron eller argument utan är fullt utvecklade och absoluta. Det skapas alltså 10 instanser av gruppen rum, där var instans pekar på samma mallfil, och har samma revisionsnummer. De har olika instansID, och olika tekniska namn (rum 1-10). Det skapas också 10 instanser av var och en av gruppens komponenter. 

Ett objekt har alltid en referens till sin mallfil objektet skapades från. 