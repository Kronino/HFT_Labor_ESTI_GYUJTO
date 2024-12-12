### **Metaadatok a megvalósítandó osztályokhoz és metódusokhoz**

---

#### **Modellek**

1. **`Book` osztály**
   - **Tulajdonságok**:
     - `int ID`
     - `string Title`
     - `int PublicationYear`
     - `Publisher Publisher` (kapcsolat)
     - `Author Author` (kapcsolat)

2. **`Author` osztály**
   - **Tulajdonságok**:
     - `int ID`
     - `string Name`
     - `List<Book> Books` (egy-a-többhöz kapcsolat)

3. **`Publisher` osztály**
   - **Tulajdonságok**:
     - `int ID`
     - `string Name`
     - `List<Book> Books` (egy-a-többhöz kapcsolat)

---

#### **Attribútum**

1. **`ValidYearAttribute`**
   - **Konstruktor paraméterei**:
     - `int MinYear`
     - `int MaxYear`
   - **Metaadat**:
     - Használható tulajdonságokon: `[AttributeUsage(AttributeTargets.Property)]`
   - **Feltételezett viselkedés**:
     - Ellenőrzi, hogy a cél tulajdonság értéke a megadott intervallumba esik-e.

---

#### **Adatbáziskezelés**

1. **`LibraryContext` osztály**
   - **Tulajdonságok**:
     - `DbSet<Book> Books`
     - `DbSet<Author> Authors`
     - `DbSet<Publisher> Publishers`
   - **Feladata**:
     - Kapcsolat konfigurálása az InMemory adatbázishoz.

---

#### **XML feldolgozása**

1. **`XmlLoader` osztály**
   - **Metódusok**:
     - `LoadFromXml(string filePath)`  
       - Visszatérési érték: `(List<Book>, List<Author>, List<Publisher>)`
       - Feladata: Beolvassa az XML-t és létrehozza az entitások listáját.

---

#### **Attribútum ellenőrzés reflexióval**

1. **`ReflectionValidator` osztály**
   - **Metódusok**:
     - `Validate(object obj)`  
       - Visszatérési érték: `bool`  
       - Feladata: Reflexióval ellenőrzi, hogy a megjelölt attribútum feltételei teljesülnek-e.

---

#### **Event használata**

1. **`EventPublisher` osztály**
   - **Események**:
     - `event Action<string> OnDataAdded`
   - **Metódusok**:
     - `Notify(string message)`  
       - Feladata: Értesítés küldése a konzolnak vagy más eseménykezelőnek.

---

#### **LINQ lekérdezések**

1. **`Queries` osztály**
   - **Metódusok**:
     - `GetBooksWithAuthors()`  
       - Visszatérési érték: `IEnumerable<string>`  
       - Feladata: Könyvek és szerzőik nevének listázása.
     - `GetPublishersWithBookCount()`  
       - Visszatérési érték: `IEnumerable<string>`  
       - Feladata: Kiadók neve és hozzájuk tartozó könyvek száma.
     - `GetBooksAfter1990()`  
       - Visszatérési érték: `IEnumerable<Book>`  
       - Feladata: 1990 után kiadott könyvek listázása.

---

#### **JSON mentés**

1. **`JsonSaver` osztály**
   - **Metódusok**:
     - `SaveResults<T>(IEnumerable<T> data, string folderPath)`  
       - Feladata: Adatok JSON formátumban történő mentése egy jelenlegi időponttal létrehozott mappába, azon belül egy Results.json fájlba.
