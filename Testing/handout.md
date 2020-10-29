@jona159
# Testing
## Test Driven Development (TDD) 
* _Kennzeichnet sich dadurch, dass zuerst die Tests geschrieben werden und erst später die Implementierung der dazugehörigen Komponenten geschieht_
* _Es wird kein Produktivcode geschrieben, es sei denn es existiert bereits ein Test welcher dies vorsieht_
* _Zyklischer Ablauf:_
    1. _Test schreiben_
    1. _Test auf Fehler überprüfen_
    1. _Code implementieren, sodass Test erfolreich durchläuft_
    1. _Sicherstellen, dass alle Tests OK sind_
    1. _Test und Produktivcode werden refaktorisiert_
* __Vorteile von TDD:__
    * _gute Wartbarkeit und Qualität (kein ungetesteter Code, saubere Struktur, Minimierung der Redundanzen)_
    * _Erhöhte Effektivität und Effizienz bei der Codeerstellung (gewünschtes Ergebnis bei minimaler Anzahl an geschriebenen Zeilen)_
## Unit Tests vs Integration Tests
 * __Unit Tests__
   * _Einzelne Codeeinheit die getestet werden soll (z.B. Funktion)_
   * _Testen auf dem niedrigsten Level_
   * _Simpler, schneller Entwurf_
   * _Reduziert Bugs, schnelleres Debugging_
   * _Tests können auch zur Dokumentation dienen_
   * _stellt die korrekte Implementierung der vorher festgelegten Bedingungen sicher_
   * _Ursache der falschen Implementierung wird schnell ersichtlich_
   
 * __Integration Tests__
   * _Zusammenhängende Systemkomponenten werden auf erfolgreiches Zusammenwirken getestet_
   * _Dabei sollen Module dem gewünschten Interaktionsprotokoll folgen_
## pytest
* Framework zum einfachen Erstellen von skalierbaren Tests
 1. **Parallel Tests**
      * _Tests sollen gleichzeitig laufen, um Zeit bei der Ausführung zu gewinnen_
      * _xdist plugin für pytest installieren_
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
          
      
 1. **Test Suites**

 1. **Most Important CLI Instructions**

 1. **writing assertions**

 1. **paths/testdata/testfiles**

 1. **temp dirs/files**

 1. **fixtures**
 
 1. **mocking**

 1. **test cache**
