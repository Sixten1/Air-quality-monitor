# Titel

Luftkvalitetsmonitor

# Funktion

Kollar om luftkvaliteten i en angiven stad, är luften bra eller bör man stanna inomhus

# Problem och koppling tillverkligheten

luftkvaliteten kan påverka både människans hälsa och miljön, men det kan vara svårt att faktiskt få en uppfattning om luftkvaliteten på olika platser. Detta projekt löser detta problem genom att hämta aktuell data och sedan värden för PM10, PM2.5 och European Air Quality Index, samt en liten text om hur luftkvaliteten är.


# Teknisk lösning

Jag har använt mig av flera olika bibliotek som har gjort detta möjligt/förenklat.
* Open-Meteo API 
Open-Meteo är ett väder-API som erbjuder korrekt och tillförlitlig väderdata som ska vara tillgänglig till alla.
* Requests
Requests är ett bibliotek som gör så att man kan skicka HTTP-förfrågningar
* CSV
Jag har använt mig av CSV-filer då det passar bra för strukturerad data. Det blir även enklare att ändra och lägga till ny data utan att ändra i koden.
* Klasser och arv
Jag har använt klasser och arv för att strukturera min kod och att samla information. Klassen Measurement fungerar som en basklass och klassen AirQualityMeasurement är en barnklass som ärver från Measurement. Jag använder arv då det gör koden mer lättläst och att jag undviker att skriva samma kod flera gånger.
* Try/except
När jag kallar på API:et så använder jag mig av Try/Except då jag vill kolla vad sidan har för status och om det är något som är fel skriver ut en felkod. Sedan så vill jag inte att programmet ska krascha om det är något fel med API:et då är try bra då den testar API:et. 
* Matplotlib
Matplotlib använder jag för att göra grafer om värdena PM10, PM2.5. Den visar datan i stapeldiagram så att det blir lättare att se de olika luftkvalitetsvärden.
* Datetime
När användaren kollar på en stads luftkvaliteten så spar jag tiden samt värdena i air_quality_data så att man kan gå tillbaka senare och jämföra.
* Användarens val av stad
Användaren får välja en stad från en numrerad lista. Programmet läser in städerna från en csv-fil. Antalet val anpassas automatiskt beroende på hur många städer som är i csv-filen. Användarens val kontrolleras med try/except och villkor så att den får bara in giltiga värden. När en stad har valts så hämtas stadens koordinater för att sedan hämta aktuell luftkvalitetsdata från API.

# Koppling till AI-utvecklarrolen

Projektet har koppling till AI-utvecklarrollen eftersom AI-utvecklare ofta arbetar med att hämta, strukturera och analysera data från olika källor. I projeket så hämtas luftkvalitetsdata från ett API, sparas i CSV-filer och visualiseras med Matplotlib. Det är relevant eftersom data ofta behöver samlas in och bearbetas innan den kan användas i analyser eller AI-modeller. 

# Resultat

Programmet frågar användaren att välja en stad från csv-filen. När användaren har valt en stad så hämtas den aktuella luftkvaliteten från Open-Meteo api.

resultatet visar stadens PM10, PM2.5 och European air quality index. Programmet tolkar även Air quality index (AQI) och visar därefter en text som beskriver om luftkvaliteten är bra, måttlig eller dålig.

Mätningen sparas också i en CSV-fil tillsammans med tidstämpel och stad, detta gör det möjligt att se tidigare körningar. PM10 och PM2.5 visas även i ett stapeldiagram med hjälp av biblioteket Matplotlib för att göra resultatet lättare att jämföra visuellt.

Exempel utskrift:

Örebro
PM10: 4.3 µg/m³
PM2.5 2.2 µg/m³
European AQI: 23
[STAPELDIAGRAM]
The European air quality index is more than 20 but less than 40 (23).
The air quality is fair

# Reflektion 

Csv hanteringen tycker jag fungerade bra, smidigt att komma igång med det och känns som att man kan ha mycket användning av det. Tycker även att Matplotlib var enklare än vad jag trodde det skulle vara, sedan tror jag att man kan göra det mer avancerat men den som jag använde fungerade bra och det var enkelt att förstå vad varje grej gjorde. Jag tycker att själva grunden i programmet var väldigt lätt att skapa, gick snabbt för mig att få till en stads PM10, PM2.5 och EAQI. 

Det jag tycker var svårt var att lyckas med var när man hade flera städer och man skulle få in i latituden och longituden. Som sagt så tyckte jag att grunden var enkel att koda, men när jag gjorde om grunden till Klasser och metoder så tyckte jag det var svårt med hur man kan använda data från en metod till en annan metod. Main(): Tog väldigt lång tid för mig att få ihop logiken. Men svårast tycker jag nästan har varit try/except med API anropet, hittade inte så mycket bra information kring detta, känner att det var lite svårt att felsöka. 

Det jag hade gjort annorlunda är nog att börja med metoder direkt. Jag började med att skriva grundprogrammet med 1 stad, tror att det kan har saktat ner mig en del. Men sedan tror jag också att det kan vara skönt att göra det också då man känner kanske att man har en bra grund. Hade jag gjort om detta så hade jag nog gjort grunden med funktioner och sedan byggt vidare från det. Men planering av programmets struktur tror jag är väldigt viktigt att göra från början. Man kanske hade kunnat skriva mer i ord hur programmet ska vara strukturerat och vad varje klass och metod ska fungera. 

Man hade kunnat vidareutvecklat detta program mer några exempel på grejer man kan göra för att förbättra är:
1. Man kan lägga till fler städer.
2. Menyn hade man också kunnat ändra när man har lagt till fler städer. Man hade kunnat välja kontinent så får man städer från de olika kontinenterna eller länder (beror lite på hur stort man vill göra det). Man hade även kunnat göra en välj alla städer, och sedan så sorterar man det i matplotlib utifrån bäst luftkvalitet. 
3. Bättre graf. Hade varit roligt om man hade kunnat se hur luftkvaliteten har ändrats i en stad. Man hade även kunnat spara data från en hel dag så man kan se när luften är som bäst.

# Github-repository
https://github.com/Sixten1/Air-quality-monitor.git

# Installation och körning


Projektet är gjort i Python och körs i en Jupyter Notebook.

För att köra projektet behövs:

- Python installerat
- Jupyter Notebook eller VS Code med Jupyter-tillägget
- Biblioteken requests och matplotlib

Biblioteken kan installeras med:

pip install requests matplotlib

För att köra projektet öppnar man notebook-filen i VS Code eller Jupyter och kör cellerna uppifrån och ned. Filen cities.csv måste ligga i samma mapp som notebook-filen eftersom programmet läser in städer och koordinater därifrån.

När programmet körs visas en lista med städer. Användaren väljer en stad genom att skriva in motsvarande nummer. Därefter hämtas aktuell luftkvalitetsdata, resultatet visas i terminalen och i ett diagram, och mätningen sparas i air_quality_data.csv.