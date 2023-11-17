## Optymalizacja wydajności w SQL Server

### Monitorowanie:
Użyj narzędzi monitorujących, takich jak Extended Events, SQL Profiler, czy Performance Monitor, aby zrozumieć obciążenie serwera i zlokalizować wąskie gardła.
Sprawdzaj wykorzystanie zasobów, takich jak procesor, pamięć, dysk i sieć, aby określić, gdzie mogą występować problemy.

### Analiza zapytań:
Przejrzyj najczęściej uruchamiane zapytania i te, które zużywają najwięcej zasobów, przy użyciu narzędzia Query Store lub Dynamic Management Views (DMV).
Przeanalizuj plany wykonania zapytań, aby zidentyfikować kosztowne operacje.

### Optymalizacja indeksów:
Przeglądaj i dostosuj indeksy; usuń te nieużywane, dodaj brakujące indeksy oraz zoptymalizuj istniejące.
Wykorzystaj Database Engine Tuning Advisor do analizy i rekomendacji.

### Architektura baz danych:
Optymalizuj schemat bazy danych; normalizacja i denormalizacja w odpowiednich sytuacjach.
Rozważ dodanie indeksów tam, gdzie są potrzebne, aby zwiększyć wydajność zapytań.
Rozważ partycjonowanie tabel w przypadku dużych zbiorów danych.

### Optymalizacja zapytań:
Zredukuj złożoność zapytań, unikaj zbędnych subzapytań i skomplikowanych łączeń.
Unikaj funkcji skalarnych i kursorów, które mogą działać wolno na dużych zbiorach danych.
Używaj zapytań parametryzowanych, aby zwiększyć wydajność poprzez ponowne wykorzystanie planów wykonania.

### Zarządzanie pamięcią i zasobami:
Skonfiguruj odpowiednio ustawienia pamięci SQL Server, aby zapewnić optymalne wykorzystanie.
Monitoruj i zarządzaj blokadami, aby uniknąć zakleszczeń i długotrwałych blokad.

### Przetwarzanie wsadowe i transakcje:
Zastosuj przetwarzanie wsadowe do dużych operacji na danych.
Zarządzaj rozmiarem i logiką transakcji, aby zminimalizować ich wpływ na wydajność.

### Konserwacja bazy danych:
Regularnie przeprowadzaj konserwację bazy danych, w tym defragmentację indeksów i aktualizację statystyk.
Monitoruj i zarządzaj rozmiarem plików bazy danych i plików logów.

### Optymalizacja konfiguracji serwera:
Skonfiguruj opcje serwera SQL, takie jak maksymalna ilość pamięci, ustawienia równoległości (MAXDOP), czy konfiguracja tempdb.

### Analiza i zarządzanie sprzętem:
Sprawdź wydajność dysków, sieci i procesorów.