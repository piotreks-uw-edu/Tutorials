## Zakleszczenie
(ang. deadlock) w bazie danych występuje, gdy dwa lub więcej procesów trzymają blokady na zasobach, których każdy z nich potrzebuje do kontynuacji działania, ale żaden nie może kontynuować, ponieważ każdy czeka na zwolnienie zasobów przez inny proces. W efekcie procesy te wpadają w nieskończony cykl oczekiwania, ponieważ każdy z nich czeka na zasób, który jest zablokowany przez inny proces w zakleszczeniu.

### Oto przykład, jak może dojść do zakleszczenia:
1. Proces A posiada blokadę na zasobie X i żąda blokady na zasobie Y.
2. W tym samym czasie Proces B posiada blokadę na zasobie Y i żąda blokady na zasobie X.
3. Żaden z procesów nie może kontynuować wykonania swoich operacji, ponieważ oba czekają na zasoby zablokowane przez drugi proces.

Systemy zarządzania bazami danych, takie jak SQL Server, wykrywają zakleszczenia za pomocą mechanizmów wykrywania zakleszczeń i automatycznie rozwiązują problem poprzez wymuszenie przerwania jednej z transakcji (nazywanej ofiarą zakleszczenia), umożliwiając kontynuację pracy pozostałym procesom. Transakcja, która zostanie przerwana, otrzymuje błąd zakleszczenia i jej operacje są cofane, a zasoby zwalniane.

### Aby zapobiegać zakleszczeniom, można stosować różne strategie, takie jak:
- Projektowanie aplikacji w taki sposób, aby transakcje były jak najkrótsze i zawsze uzyskiwały blokady w tej samej kolejności.
- Używanie niższych poziomów izolacji transakcji, jeśli scenariusz biznesowy na to pozwala.
- Analiza i optymalizacja zapytań, aby unikać nadmiernego blokowania.
- Używanie instrukcji TRY/CATCH w kodzie T-SQL, aby łatwiej zarządzać błędami i powtórzeniami transakcji w przypadku wystąpienia zakleszczenia.




