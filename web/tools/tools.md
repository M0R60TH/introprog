I denna kurs använder vi programmeringsspråket **Scala** och exekveringsmiljön **OpenJDK**, samt byggverktyget `sbt` och editorn `vscode`. Läs om hur du använder dessa och andra programmeringsverktyg i **Appendix** i [kompendiet](https://cs.lth.se/pgk/compendium/). Verktygen finns förinstallerade på LTH:s [Linuxdatorer i E-huset](https://www.lth.se/lthin/datorsalar/vaara-datorsalar/e-huset/). Instruktioner om hur du installerar dessa verktyg på din egen dator finns i Appendix i kompendiet och nedan.

## Programmera på LTH:s datorer

På LTH:s [Linuxdatorer i E-huset](https://www.lth.se/lthin/datorsalar/vaara-datorsalar/e-huset/) finns alla de verktyg vi använder i kursen förinstallerade:

* Rekommenderad kodeditor: VS Code startas med kommandot `code`
* Scala REPL; kommando: `scala`
* Utvecklingsmiljön Kojo; kommando: `kojo`
* Scala-kompilatorn; kommando: `scalac`
* Byggverktyget sbt; kommando: `sbt`
* Java-kompilatorn; kommando: `javac`
* Exekveringsmijlön JVM med tillhörande utvecklingsbibliotek (OpenJDK); kommando: `java`
* Utvecklingsmiljön IntelliJ IDEA med Scala-plugin; kommando: `idea`


## Programmera på din egen dator 

Du behöver följande verktyg på din egen dator: Kojo, OpenJDK, sbt, VS Code med tillägget Scala (Metals). Läs om dessa i Appendix i [kompendiet](https://cs.lth.se/pgk/compendium/) och följ instruktionerna nedan om hur du installerar verktygen på din egen dator.


### Installera Kojo

Följ instruktioner här: [http://www.kogics.net/kojo-download](http://www.kogics.net/kojo-download)

Vi använder utvecklingsmiljön Kojo på första labben. Kojo är utvecklat speciellt för att hjälpa elever i grundskola och gymnasium att lära sig programmera. Kojo används på [Vattenhallen Science Center](https://www.vattenhallen.lu.se/upplevelser/programmering/). 

LTH-studenter med programmeringskunskaper och intresse för pedagogik är välkomna att ansöka om att bli programmeringshandledare i Vattenhallen här: [https://www.vattenhallen.lu.se/om-oss/kontakt/vh-student/student-intresseanmalan/](https://www.vattenhallen.lu.se/om-oss/kontakt/vh-student/student-intresseanmalan/)


### Installera kodeditor

* [**VS Code**](https://code.visualstudio.com/): rekommenderas i kursen, öppen källkod, alla plattformar. Installera tillägget **Scala Metals** via editorns tilläggshanterare (Extensions Ctrl+Shift+X), skriv i sök-rutan: *Metals*

* [Atom](https://atom.io/): öppen källkod, alla plattformar, paketet Scala Metals finns att installera i editorns tilläggshanterare.

* [Sublime Text](http://www.sublimetext.com/): stängd källkod, alla plattformar, paketet Scala Metals finns att installera i editorns tilläggshanterare.

Läs mer om vad du kan göra med en kodeditor i appendix i [kompendiet](https://cs.lth.se/pgk/compendium/) 


### Starta terminalfönster

Många av de programmeringsverktyg vi använder körs via ett terminalfönster. Du startar ett terminalfönster såhär:

* **Linux/Ubuntu**: Tryck Ctrl+Alt+T eller tryck på Windows-tangenten och sök efter "Terminal". 

* **Windows**: 
    * För Windows rekommenderas Microsoft-appen "Windows Terminal", se vidare här: [https://docs.microsoft.com/en-us/windows/terminal/get-started](https://docs.microsoft.com/en-us/windows/terminal/get-started) 
    * Om du har en uppdaterad version av **Windows 10** och en någorlunda modern dator så rekommenderas **WSL2** som ger dig tillgång till Linux/Ubuntu direkt under Windows, följ instruktioner här och välj Ubuntu 20.04 (fråga ngn om hjälp om du kör fast):  [https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
    * Du kan också köra den befintliga cmd-terminalen som inte kräver någon installation, följ instruktioner här [https://www.howtogeek.com/235101/10-ways-to-open-the-command-prompt-in-windows-10/](https://www.howtogeek.com/235101/10-ways-to-open-the-command-prompt-in-windows-10/) 

* **Mac**: Följ instruktioner här: [https://www.howtogeek.com/682770/how-to-open-the-terminal-on-a-mac/](https://www.howtogeek.com/682770/how-to-open-the-terminal-on-a-mac/)


### Installera Java Development Kit (JDK)

**Kontrollera om du redan har JDK: **
Du kanske redan har JDK installerat. Kontrollera detta genom att i ett terminalfönster skriva (observera avslutande c:et):

```
javac -version
```

Version 11 rekommenderas, men andra versioner kan ev. också fungera. Om utskriften säger att `javac` saknas, installera då OpenJDK enl. nedan.

**Installera OpenJDK: **  Läs även instruktionerna i appendix i [kompendiet](https://cs.lth.se/pgk/compendium/) innan du sätter igång.

* Windows/Mac: Installera OpenJDK här [https://adoptopenjdk.net/](https://adoptopenjdk.net/)
 
    1. Välj att ladda ner OpenJDK **version 11**  (LTS) HotSpot **för ditt operativsystem**.
    2. I hämtade filer dubbelklicka för installation med förifyllda val.
    3. Starta om din dator.
    4. Starta terminalfönster och kontrollera enligt ovan att `javac` och `java` ger rätt version.
        * Om något krånglar: fråga någon som installerat JDK förr om hjälp. 

* Linux/Ubuntu/WSL: Öppna terminalfönster och kör:
    `sudo apt install openjdk-11-jdk`



### Gör `scala` och `scalac` tillgängligt i terminalen

* **Linux/Ubuntu/WSL/MacOS**: Scala installeras lättast med **sdkman**:
    * Testa att nedladdningsprogrammet `curl` finns på ditt system genom att skriva `curl --version` i terminalen. Om `curl` saknas så installera detta i terminalen genom att skriva:
    ```
    sudo apt install curl
    ```
    * Om du inte redan gjort det, installera **sdkman** genom att öppna ett terminalfönster och kopiera och klistra in följande, en rad i taget:
    ```
    curl -s "https://get.sdkman.io" | bash
    source "$HOME/.sdkman/bin/sdkman-init.sh"
    ```
    * Installera Scala med kommandot `sdk` så här:
    ```
    sdk install scala
    ```  
    * Starta ett *nytt* terminalfönster och testa att skriva `scala -version` och om allt gått bra ska du få en utskrift som börjar med "Scala compiler version".
    
* **Windows**: För att ladda ner och installera Scala så att `scalac` och `scala` blir tillgängligt i terminalen i Windows, gör så här:
    * Installera OpenJDK enligt instruktioner ovan. 
    * Ladda ned filen install-scala.bat via länken [https://cs.lth.se/pgk/scala-windows](https://cs.lth.se/pgk/scala-windows) och spara den t.ex. i Downloads och dubbel-klicka på den. Ett terminalfönster öppnas och kör igång nedladdning och uppdatering av path. När den är klar är det bara att starta en ny terminal och köra `scala`.
        * För att installera en specifik version av scala så kan man i terminalen ge versionsnummer som argument, t.ex:
            ```
            install-scala.bat 3.1.0-RC1
            ```
    * Om du har tillräckligt ny Windows-maskin rekommenderas även WSL (se ovan under "Starta terminalfönster") som gör att du kan köra Linux/Ubuntu under Windows och då installera ovan verktyg enligt instruktioner för Linux. 
    * Det finns också några lovande alternativ under utveckling som ska göra det ännu enklare att komma igång med Scala, där `scala-cli` rekommenderas:
        * `scala-cli` är ett nytt program som enkelt och smidigt kan kompilera och göra igång scala-program och REPL. Installera [msi-filen som är specifik för Windows](https://github.com/VirtuslabRnD/scala-cli/releases/download/nightly/scala-cli-x86_64-pc-win32.msi) och läs mer om hur man använder `scala-cli` i terminalen här: [https://virtuslabrnd.github.io/scala-cli/](https://virtuslabrnd.github.io/scala-cli/) 
        * [Coursier](https://get-coursier.io/docs/cli-installation#windows) är ett avancerat system för installation och nedladdning som i sin tur kan installera kommandot `scala3-compiler` och `scala3-repl`. Kompilerade program måste tyvärr i skrivande stund köras direkt med `java`-kommandot, se längre ned i detta ärende: [https://github.com/coursier/coursier/issues/2058](https://github.com/coursier/coursier/issues/2058) 


### Installera byggverktyget `sbt`

Installera Scala Build Tool `sbt`: 

* **Linux/Ubuntu/WSL/MacOS**: 
    * Installera **sdkman** om du inte redan gjort det (se ovan).
    * Installera genom att skriva detta kommando i terminalen:
      ```
      sdk install sbt
      ```
    * Starta ett *nytt* terminalfönster och testa att skriva `sbt -version` och om allt gått bra ska du efter ett tag få en utskrift som börjar med "sbt version". 

* **Windows**: Ladda ner och kör [https://github.com/sbt/sbt/releases/download/v1.5.5/sbt-1.5.5.msi](https://github.com/sbt/sbt/releases/download/v1.5.5/sbt-1.5.5.msi)

Läs mer om hur du använder `sbt` i Appendix i [kompendiet](https://cs.lth.se/pgk/compendium/). 



## Hårdvara

Vid undervisning på campus rekommenderas LTH:s [Linux-datorer](https://www.lth.se/lthin/datorsalar/vaara-datorsalar/e-huset/). Ta gärna med ett eget tangentbord och en egen mus och koppla in i skolans datorer så minskar du smittrisken. 

När du studerar hemma behöver du en bra arbetsplats och en dator med Linux (t.ex. Ubuntu 20.04), Windows 10 eller Mac. Det är bra att ha en ergonomisk kontorsstol vid ett bekvämt skrivbord, ett flyttbart tangentbord, en separat mus och en höj-och-sänkbar skärm.

### Köpa egen dator

När du ska programmera är det bra med en dator med minst 8GB RAM och 2.5GHz CPU. Du kan t.ex. köpa dator här: [Compliq i Lund](https://www.compliq.se/bygga-dator/), [Webbhallen i Malmö](https://www.webhallen.com/se/store/22-Malmo-Triangeln), [Inet i Malmö](https://www.inet.se/info/243/inet-malmo)

Både [Lenovo](https://www.lenovo.com/se/sv/studentrabatt/) och [Dell](https://www.dell.com/sv-se/shop/dell-advantage/cp/students) har studentrabatt och säljer både stationära och bärbara datorer. De har även datorer med [Linux förinstallerat](https://news.itsfoss.com/best-linux-laptops-2021/).

Om du letar efter en bra stationär dator rekommenderas senaste modellen av [Siago](https://www.atlastsolutions.com/sigao/) som är fläktlös och därmed helt tyst. Sigao kan fås med Ubuntu eller Windows förinstallerat.

### Headset-adapter

Vid distansundervisning är det bra med headset och webbkamera. Det går bra att koppla ditt eget headset till skolans datorer, t.ex. om du behöver prata med en handledare som jobbar hemifrån. Enklast är att använda ett USB-headset då kontakten sitter på framsidan. Om du har ett headset med 4-polig mobil-kontakt medan din dator har två 3-poliga kontakter för mic och hörlurar behövs en sådan här adapter:

<img src="https://github.com/lunduniversity/introprog/raw/master/web/tools/adapter.jpg" alt="drawing" style="width:200px;"/>

Kan t.ex. köpas här: 
[NetOnNet](https://www.netonnet.se/art/ljud-bild/kablar/adapter/andersson-computer-headset-adapter-female/1006756.13721/), 
[Elgiganten](https://www.elgiganten.se/product/ljud-hifi/ljudkablar-adapters/HAMA54572/hama-3-5-mm-adapter-for-headset-med-mikrofon), 
[Webhallen](https://www.webhallen.com/se/product/313979-iiglo-Multimedia-adapter-till-Dator-Svart), 
[Kjell](https://www.kjell.com/se/produkter/dator/horlurar-headset/tillbehor-for-horlurar-headset/datoradapter-for-mobil-headset-p39356), 
[Mediamarkt](https://www.mediamarkt.se/sv/product/_deltaco-ljudadapter-3-5mm-mikrofon-3-5mm-stereo-hane-till-3-5mm-hona-4-pin-0-1-m-1305626.html), 
[Inet](https://www.inet.se/produkt/8904289/deltaco-adapter-2x3-5mm-ha-till-3-5mm-ho-4-pin-0-1m-svart)
