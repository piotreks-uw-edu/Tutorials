## Oto kilka podstawowych rodzajów blokad używanych w SQL Server:

### Shared Locks (S)
Blokady współdzielone umożliwiają odczyt zasobu przez wiele transakcji. Inne transakcje mogą jednocześnie odczytywać zablokowany zasób, ale żadna nie może go zmodyfikować do czasu zwolnienia blokady.

### Exclusive Locks (X)
Blokady wyłączne są stosowane, gdy transakcja chce zmodyfikować zasób, np. podczas operacji INSERT, UPDATE, lub DELETE. Taka blokada zapobiega innym transakcjom odczytu lub modyfikacji zasobu do czasu jej zwolnienia.

### Update Locks (U)
Blokady aktualizacyjne są stosowane w sytuacjach, gdy transakcja ma zamiar zmodyfikować zasób, ale nie jest jeszcze gotowa do nałożenia blokady wyłącznej. Dzięki temu inne transakcje mogą odczytywać zasób, ale nie mogą go zmodyfikować ani nałożyć na niego własnej blokady aktualizacyjnej.

### Intent Locks
Są to blokady, które sygnalizują zamiar nałożenia bardziej szczegółowej blokady na niższym poziomie hierarchii blokad. Wyróżniamy:
- Intent Shared (IS): Sygnalizuje zamiar nałożenia blokad współdzielonych na niższym poziomie.
- Intent Exclusive (IX): Sygnalizuje zamiar nałożenia blokad wyłącznych na niższym poziomie.
- Shared with Intent Exclusive (SIX): Sygnalizuje zamiar nałożenia blokady współdzielonej na bieżącym poziomie i blokad wyłącznych na niższych poziomach.
- Schema Locks: Blokady schematu są stosowane podczas operacji, które wpływają na strukturę obiektów bazy danych:

### Schema Modification (Sch-M)
Nałożona podczas operacji modyfikującej schemat, np. ALTER TABLE.
Schema Stability (Sch-S): Utrzymywana podczas operacji, które są zależne od schematu, np. kompilacji zapytań.
Bulk Update Locks (BU): Są to blokady stosowane podczas operacji masowych ładowań danych, kiedy transakcja używa klauzuli TABLOCK.

### Key-Range Locks
Blokady zakresu kluczy są stosowane w operacjach z indeksami, aby zapobiegać wstawianiu lub modyfikacji wierszy w zakresie indeksu przez inne transakcje, co jest istotne na poziomie izolacji SERIALIZABLE, aby zapobiegać tzw. "phantom reads".