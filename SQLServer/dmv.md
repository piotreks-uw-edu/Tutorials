## Oto niektóre z najczęściej używanych DMVs, z którymi powinni być zaznajomieni DBA:

### sys.dm_exec_requests
Dostarcza informacji o każdym żądaniu, które jest obecnie wykonywane.

### sys.dm_exec_sessions
Pokazuje wszystkie aktywne połączenia użytkowników i wewnętrzne zadania.

### sys.dm_exec_query_stats
Oferuje zbiorcze statystyki wydajności dla buforowanych planów zapytań.

### sys.dm_os_wait_stats
Wyświetla statystyki oczekiwania dla wszystkich typów oczekiwania.

### sys.dm_db_index_usage_stats
Zwraca liczbę różnych typów operacji na indeksach i czas ostatniego wykonania każdego typu operacji.

### sys.dm_db_index_physical_stats
Daje szczegółowe informacje o fizycznej strukturze indeksów, takie jak fragmentacja.

### sys.dm_os_memory_clerks
Dostarcza informacji o alokacji pamięci przez różne komponenty SQL Server.

### sys.dm_os_performance_counters
Wyświetla wartość liczników wydajności SQL Server.

### sys.dm_tran_locks
Pokazuje informacje o aktualnie aktywnych zasobach menedżera blokad.

### sys.dm_io_virtual_file_stats
Zwraca statystyki I/O dla plików danych i logów.

### sys.dm_exec_sql_text
Przyjmuje uchwyt SQL jako argument i zwraca tekst partii SQL, który jest identyfikowany przez ten uchwyt.

### sys.dm_exec_cached_plans
Zwraca wiersz dla każdego planu zapytania, który jest buforowany przez SQL Server w celu szybszego wykonania zapytania.

### sys.dm_exec_query_plan
Przyjmuje uchwyt planu jako argument i zwraca odpowiadający mu plan wykonania.

### sys.dm_db_missing_index_details
Zwraca szczegółowe informacje o brakujących indeksach, w tym uchwyt grupy, unikalne kompilacje i poszukiwania użytkowników.

### sys.dm_os_sys_info
Dostarcza informacji o systemie, takich jak liczba procesorów, pamięć i użycie zasobów przez SQL Server.

Te DMVs są potężnymi narzędziami do diagnozowania problemów i dostrojenia wydajności instancji SQL Server. 