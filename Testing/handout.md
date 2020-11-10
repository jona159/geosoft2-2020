@jona159

# Testing

## Test Driven Development (TDD) 

* _Kennzeichnet sich dadurch, dass zuerst die Tests geschrieben werden und erst später die Implementierung der dazugehörigen Komponenten geschieht_
* _Es wird kein Produktivcode geschrieben, es sei denn es existiert bereits ein Test welcher dies vorsieht_
* _Begriff __Codeabdeckung:__ prozentualer Anteil des Gesamtcodes, der durch Tests ausgeführt wird_
* _Zyklischer Ablauf:_
    1. _Test schreiben_
    1. _Test schlägt (quasi zum Beweis) mindestens einmal fehl_
    1. _gerade soviel Code implementieren, sodass Test erfolreich durchläuft_
    1. _Sicherstellen, dass alle Tests bestehen (,,pass")_
    1. _Test und Produktivcode werden refaktorisiert (verbessert)_

* __Vorteile von TDD:__

    * _gute Wartbarkeit und Qualität (kein ungetesteter Code, saubere Struktur, Minimierung der Redundanzen)_
    * _Erhöhte Effektivität und Effizienz bei der Codeerstellung (gewünschtes Ergebnis bei minimaler Anzahl an geschriebenen Zeilen)_
    * _Entwickler denken über Testszenarien nach, bevor sie den Code implementieren_
    * _schnelle Offenlegung von schlecht entworfenem, monolithischem Code_
    * _Tester sind gegenüber dem Code nicht voreingenommen und fördern oftmals Mängel zutage, die den Entwicklern nicht aufgefallen sind_
    * _Abhängigkeiten von Funktionen können umgangen oder nachgeahmt werden, sodass man sich auf den Code konzentrieren kann der getestet werden soll_
    
    
* __Quellen:__ 

    * [Youtube Vortrag](https://www.youtube.com/watch?v=IvqX-HTd8o0) (v.a. ab 9:30min)
    * [Einführung in TDD](https://medium.com/hackernoon/introduction-to-test-driven-development-tdd-61a13bc92d92)
    * [TDD Vorteile](https://www.it-agile.de/wissen/agiles-engineering/testgetriebene-entwicklung-tdd/) 
    
## Unit Tests vs Integration Tests

 * __Unit Tests__
 
   * _Einzelne Codeeinheit die getestet werden soll (z.B. Funktion)_
   * _Testen auf dem niedrigsten Level_
   * _Simpler, schneller Entwurf_
   * _Reduziert Bugs, schnelleres Debugging_
   * _Tests können auch zur Dokumentation dienen_
   * _stellt die korrekte Implementierung der vorher festgelegten Bedingungen sicher_
   * _Ursache der falschen Implementierung wird schnell ersichtlich_
  * Beispiel aus GeoSoft1 ([Streuselcake repository](https://github.com/streuselcake/jslab/blob/master/utils/unittest/qunit/test.js)): 
  ```
  // is fair coin?
QUnit.test( "Coin Test in HTML (is fair coin?)", function( assert ) {

  var lim = 1000;     // coin throws
  var delta = 0.01;   // allowed delta margin for accepting coin in percent
  var headscount = 0; // number of times the coin returned head

  var c1 = new Coin(1);
  c1.observe = true;

  var results = [];

  for(var i=0; i<lim; ++i){
    headscount += c1.isHeads() ? 1 : 0;
  }

  console.log("headscount: ", headscount);
  console.log("lower bound: lim/2.0 - delta*lim", lim/2.0 - delta*lim);
  console.log("upper bound: lim/2.0 + delta*lim", lim/2.0 + delta*lim);

  assert.ok(lim/2.0 - delta*lim < headscount, "not too few heads...");
  assert.ok(lim/2.0 + delta*lim > headscount, "not too many heads...");


});
```
   
 * __Integration Tests__
 
   * _Zusammenhängende Systemkomponenten werden auf erfolgreiches Zusammenwirken getestet_
   * _Dabei sollen Module dem gewünschten Interaktionsprotokoll folgen_
 * Quelle: 
    * [Stackoverflow](https://stackoverflow.com/questions/5357601/whats-the-difference-between-unit-tests-and-integration-tests)
    
## pytest

* Framework zum einfachen Erstellen von skalierbaren Tests
* Installation:
```
pip install -U pytest
```
* __pip:__ Verwaltungsprogramm für Python packages (_"pip installs packages"_)

* [Pytest Dokumentation](https://docs.pytest.org/en/stable/contents.html)
* _tiefergehende Quellen:_
  * [Pytest Tutorial Youtube 1 Std](https://www.youtube.com/watch?v=bbp_849-RZ4)
  * [Pytest Tutorial Youtube 20min](https://www.youtube.com/watch?v=byaxg00Gf9I)
  * [Pytest Quickstart Leseprobe](https://books.google.de/books?hl=de&lr=&id=aB9sDwAAQBAJ&oi=fnd&pg=PP1&dq=pytest+testsuite&ots=dEzwW_4us2&sig=e9VJktln_8igpFiEM5q4CAYkKwQ#v=onepage&q=pytest%20testsuite&f=false)

 1. **Parallel Tests**
 
      * _Tests sollen gleichzeitig auf verschiedenen Systemen laufen, um Zeit bei der Ausführung zu gewinnen_
      * _Bei unterschiedlichen Software-Versionen prüft man auf Konsistenz und mögliche auftretende Probleme_
      * __xdist__ _plugin für pytest installieren_
         * _Installation über:_
            ```
            pip install pytest-xdist
            ```
      * _Ausführen der Tests mit:_
          ```
          pytest -n auto
          ```
          _oder_
          ```
          pytest -n 2
          ``` 
      * Quellen:
          * [Parallel Testing Introduction](https://www.guru99.com/parallel-testing.html)
          * [Pytest Parallel](https://www.tutorialspoint.com/pytest/pytest_run_tests_in_parallel.htm)
          * [xdist Dokumentation](https://docs.pytest.org/en/3.0.1/xdist.html) 
            * _weitere optionale, tiefergehende Quellen:_ 
              * [Python Parallel Testing Youtube](https://www.youtube.com/watch?v=IW_rR7Y6dbM)
              * [xdist Projektbeschreibung](https://pypi.org/project/pytest-xdist/)
      
      
 1. **Test Suites**
 
     * Eine Test Suite beschreibt im Detail eine Menge von Testfällen, sowie deren genauen Anwendungsziele [Test Suite Wikipedia](https://en.wikipedia.org/wiki/Test_suite)
     * pytest kann für die meisten bereits existierenden Test Suites verwendet werden
     * [Using pytest with an existing test suite](https://docs.pytest.org/en/latest/existingtestsuite.html)     

 1. **Most Important CLI Instructions**
 
    * `pytest` _(führt alle Tests im cd aus)_
    * `pytest --version` _(zeigt die Version von pytest an)_
    * `pytest --fixtures` _(zeigt verfügbare fixtures)_
    * `pytest --help oder pytest -h` _(Hilfeaufruf)_
    * `pytest -x` _(stoppt Testvorgang nachdem der erste Test fehlschlägt)_
    * `pytest --maxfail=x` _(stoppt Testvorgang nachdem der x-te Test fehlschlägt)_
    * `pytest --lf` _(führt die letzten fehlgeschlagenen Tests aus)_
    * `pytest exampletest_mod.py` _(führt Tests im angegebenen Dokument aus)_
    * `pytest testing/` _(führt Tests im angebenen Ordner aus)_
    * __Quelle__:
      * [pytest CLI](https://docs.pytest.org/en/stable/usage.html)
      
    * __Marker__: 
    
      * Alle markierten Tests werden ausgeführt, nicht markierte Tests werden vernachlässigt
      * Beispiel für Markierung : 
      ```
      @pytest.mark.webtest
      def test_send_http():
      pass 
      ```
      * Ausführen des markierten Tests mit: `pytest -v -m webtest` 
      * Ausführen aller nicht markierten Tests mit: `pytest -v -m "not webtest" `
 1. **writing assertions**
 
     * Das in Python inbegriffene __assert__ lässt sich auch mit pytest zum Abgleichen und Überprüfen verwenden 
     * [simples Beispiel assert, Test schlägt fehl](https://docs.pytest.org/en/stable/assert.html):
     ```
     def f(): 
       return 3
     
     def test_function():
       assert f() == 4
       ``` 
     
      * Über das __raise-statement__ kann man eine bestimmte Exception erzwingen (im Beispiel oben: _ValueError_)
         * Quelle: [raise-statement](https://docs.python.org/3/tutorial/errors.html)
      * [Beispiel youtube](https://www.youtube.com/watch?v=R7u8xWXCbGM): 
     ```
     # content of test_sample.py
     def validate_age(age):
      if age<0
       raise ValueError("Age cannot be less than 0")
       
     def test_validate_age_valid_age():
        validate_age(10)
        
     def test_validate_age_invalid_age():
        validate_age(-1)
       
      ```
      * Das __with-statement__ ersetzt Code, der sonst mit __try__...__finally__ geschrieben werden würde
        * Quelle [with-statement](https://docs.python.org/2.5/whatsnew/pep-343.html)
      * Beispiel: [Assertion für erwartete Exception](https://docs.pytest.org/en/3.0.1/assert.html) 
      ``` 
      def test_zero_division():
        with pytest.raises(ZeroDivisionError):
          1 / 0
       ```
       
 1. **paths/testdata/testfiles**
 
     * Ausführen aller Tests in files mit Namen __...test.py__ und **test___.py** über `pytest` im current directory und in Subordnern
     * Wenn man nicht im cd arbeiten möchte kann man ein directory mit `pytest` + *Pfad* angeben, z.B. : `pytest tests/../..`
     * Man kann auch mit einem Befehl mehrere directories/files angeben, z.B.: `pytest tests/../.. tests/test.py`
     * einzelne Tests innerhalb eines Files lassen sich mit `pytest` + *Test-File* + *Testfunktionsname* ausführen
     * Quelle (Kapitel _Running Tests_): [pytest Quickstart](https://books.google.de/books?hl=de&lr=&id=aB9sDwAAQBAJ&oi=fnd&pg=PP1&dq=pytest+testsuite&ots=dEzwW_4us2&sig=e9VJktln_8igpFiEM5q4CAYkKwQ#v=onepage&q=pytest%20testsuite&f=false)
     
 1. **fixtures**
 
     * Fixures sind Funktionen, die vor dem Test laufen dem sie zugeordnet sind 
     * Ein fixture ist die Umgebung in welcher der Test läuft, bspw. eine Datenbank 
       * Quelle: [codemaven.com](https://code-maven.com/temporary-files-and-directory-for-pytest)
     * fixtures initialisieren Testfunktionen als übergebene Argumente, sodass die Tests verlässlicher ausführbar, konsistenter und leichter wiederholbar werden
     * fixtures haben explizite Namen, sind modular und skalierbar
     * fixture definieren mit `@pytest.fixture` (_optional mit Parametern ,bspw. :_ `@pytest.fixture(scope=module)`)
     * In pytest sind bereits eine Reihe von fixtures inbegriffen: [pytest fixtures](https://docs.pytest.org/en/stable/fixture.html)
     * fixtures können auch andere fixtures aufrufen
     * fixtures können auch getestet werden
       
       
  1. **temp dirs/files**
  
      * Temporary directory: Ordner zum Speichern von temporären Dateien
      * [temporary directories and files](https://docs.pytest.org/en/stable/tmpdir.html)
      * __tmpdir__: fixture zum standardisierten Erstellen von temporary directories 
      * __tmp_path__ : fixture zum Erstellen eines eindeutigen temporary directory
      
 1. **mocking/patching (engl. Mock=Attrape)**
 
     * _wird verwendet wenn sich Platzhalter statt der echten Objekte beim Testen besser eignen, zum Beispiel bei API-Abfragen, da man beim Testen nicht jedesmal wieder die API-
        Abfrage durchführen möchte weil diese das Testen stark verlangsamen würde_
     * _UnitTests von Funktionen mit zu vielen Abhängigkeiten werden vereinfacht_   
     * weitere Anwendungsbereiche von mocking: 
        * _das zu testende Objekt liefert nicht-deterministische Ergebnisse, bspw: Uhrzeit_
        * _das echte Objekt existiert noch gar nicht_
        * _schwierig auslösbares Verhalten (z.B. Netzwerkzugriff)_
        * (bei Integrationstests ist mocking normalerweise nicht notwendig)
     * die wichtigsten Mocking-Typen: 
       * _Dummy: Objekt, das weitergereicht, aber nicht benutzt wird_
       * _Fake: Objekt mit eingeschränkter Implementierung_
       * _Mock: Objekt das bei Funktionsaufrufen mit übergebenen Werten eine Rückgabe liefert (erfordert die Verwendung eines mocking-Frameworks)_
     * Quelle: [wikipedia Mock-Objekt](https://de.wikipedia.org/wiki/Mock-Objekt)  
     * Pytest Mocking-Framework: __Pytest-Mock__
     * stellt __mocker__ fixture zur Verfügung
     * Installation über: 
       ```
       pip install pytest-mock
       ```
      * [pytest mocking](https://medium.com/analytics-vidhya/mocking-in-python-with-pytest-mock-part-i-6203c8ad3606)
      * [Pytest Mock Youtube Vortrag](https://www.youtube.com/watch?v=k99HSHQDsi4) (ab 14:55 min)
      * [Codefellows](https://codefellows.github.io/sea-python-401d7/lectures/mock.html) (tiefergehend)
      * [github pytest-mock](https://github.com/pytest-dev/pytest-mock) (tiefergehend)
      * [Beispiel Stackoverflow:](https://stackoverflow.com/questions/53434986/using-mocker-to-patch-with-pytest)
      ```
      import pytest


     def sum(a, b):
      return a + b


     def test_sum1(mocker):
      mocker.patch(__name__ + ".sum", return_value=9)
      assert sum(2, 3) == 9


    def test_sum2(mocker):
     def crazy_sum(a, b):
        return b + b

      mocker.patch(__name__ + ".sum", side_effect=crazy_sum)
      assert sum(2, 3) == 6
     ``` 
      
      * **//**_(optional, nur bei Interesse anschauen)_
      * __Monkeypatching__ :
         * monkeypatch ist Teil der pytest-mock library
         * das monkeypatch fixture stellt einige nützliche Hilfsfunktionen zur Verfügung (siehe Links) 
         * Quellen:
           * [Monkeypatching pytest doc](https://docs.pytest.org/en/stable/monkeypatch.html)
           * [Monkeypatching Beispiele](https://codefellows.github.io/sea-python-401d7/lectures/mock.html) 
                  
 1. **test cache**
 
     * Pytest Cache-Framework: __Pytest-Cache__
     * Installation: 
     ```
     pip install pytest-cache
     ```
     * Inhalt des Cache anschauen: 
     ```
     pytest --cache
     ```
     * Cache leeren:
     ```
     pytest --clear-cache
     ```
     * [Pytest Cache](https://pypi.org/project/pytest-cache/#:~:text=pytest%2Dcache%201.0&text=cache%20object%20which%20helps%20sharing,from%20the%20last%20run%20first.)
       (empfohlen) 
     * [Cache Usage](https://docs.pytest.org/en/6.1.2/cache.html) (tiefergehend)
