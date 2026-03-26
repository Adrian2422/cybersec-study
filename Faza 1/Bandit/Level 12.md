Link: [Level 12](https://overthewire.org/wargames/bandit/bandit12.html)

Zadaniem jest znalezienie hasła w pliku `data.txt`, gdzie wszystkie małe i duże litery zostały przesunięte o 13 pozycji

1. Plik `data.txt` jest nieczytelny więc należy odkodować szyfr cezara
2. Szukam informacji o ROT13 i jakim narzędziem go odwrócić
3. Czytam manual `man tr`
4. Używam `tr` podając źródłowy alfabet oraz jego zamiennik
5. Finalna komenda: `tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt`