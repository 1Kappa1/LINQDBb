#  LINQDb e SQLite Step by Step
1° Creare una cartella con cognome.nome.4H.Firstdb

2° Lanciare il visual studio code e aprire la cartella appena creata

3° Lanciare un terminale in visual studio code (Comando rapido: CTRL + ò)

4° Copiare il seguente comando nel terminale

``` 
dotnet new console 
```

5° Ora cliccare <a href = "https://www.sqlitetutorial.net/sqlite-sample-database/">qui</a>, si aprirà la pagina dove sarà possibile scaricare il database di prova che si troverà nella sezione Download SQLite sample database, quindi scaricarlo

6° Una volta scaricato spostarlo nella stessa cartella del nostro progetto

7° Riaprire la finestra Visual Studio Code aperta in precedenza 

8° Installare il plugin per visual studio code di nome SQLite, la cui icona è riportata qui sotto

<img 
src="https://user-images.githubusercontent.com/116791222/234798006-06c01e35-cd3f-4772-ab83-5b305904634a.png"
/>

9° Fare pulsante destro su chinook.db da dentro Visual Studio Code e cliccare "Open Databse"

10° Ora entrare nel csproj e cercare la seguente riga di codice `<PackageReference Include="sqlite-net-pc1" Version="1.8.116"`
 
11° Se non è presente copiare e incollare il seguente comando nel terminale:

```
dotnet add package sqlite-net-pcl
``` 

12° Copiare e incollare il seguente codice nel proprio programma e successivamente scrivere nel terminale `dotnet run`:

```csharp
using SQLite;

//Connessione al Database
SQLiteConnection cn1 = new SQLiteConnection("chinook.db");

//Richieste al Database
var tblArtists = cn1.Query<Artist>("select * from artists");

//Stampa su console di quanti record sono presenti in tblArtists
Console.WriteLine($"In questa tabella ci sono {tblArtists.Count} record!");

//Language Integrate Query
//LINQ

tblArtists = tblArtists.OrderByDescending(x=>x.Name).ToList();
foreach(var artista in tblArtists)
{
    Console.WriteLine($"{artista.Name}");
}



//Classe di contenimento dei dati
public class Artist
{
    public int ArtistId{get;set;}
    public string Name{get;set;}
}
```

### !!Ricordo che SQLite non è un Databse, ma una libreria!!

## Spiegazione di LINQDBb e del suo funzionamento
(Language Integrated Query) è un componente del framework .NET che permette di eseguire query su diversi tipi di dati, come ad esempio oggetti, database, XML e servizi web, in modo integrato e dichiarativo nel linguaggio di programmazione utilizzato (ad esempio C# o VB.NET).

La caratteristica principale di LINQ è la sua sintassi dichiarativa, che permette di scrivere query usando parole chiave simili a quelle utilizzate nel linguaggio SQL, come from, where, select, orderby e groupby. In questo modo, la scrittura delle query diventa più facile e leggibile rispetto alla creazione di query "manuali" usando il linguaggio di programmazione.

```csharp
var result = from element in sequence
             where element.Property == value
             orderby element.Property ascending
             select new
             {
                 Property1 = element.Property1,
                 Property2 = element.Property2
             };
```

LINQ supporta anche la composizione di query, ovvero la possibilità di concatenare più operazioni di query per creare query più complesse. Inoltre, LINQ offre una vasta gamma di operatori di query integrati, come ad esempio Count, Sum, Average, Max e Min, che semplificano ulteriormente la creazione di query.

Grazie alla sua flessibilità e potenza, LINQ è diventato uno strumento essenziale per molti sviluppatori .NET. LINQ consente di scrivere codice più conciso, leggibile e mantenibile per manipolare e interrogare dati in diversi contesti, migliorando la produttività e riducendo la possibilità di errori.
                                                                                                                                                                      
## Facoltativo
Se volete avere una visione più comoda del vostro Database installare l'estensione SQLite Viewer, l'icona è la sequente:

<img src="https://user-images.githubusercontent.com/116791222/236402603-8a404d5f-95af-44bf-aa82-711673297c89.png"/>
