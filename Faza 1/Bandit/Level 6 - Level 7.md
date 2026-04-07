Link: [Level 7](https://overthewire.org/wargames/bandit/bandit7.html)

Zadaniem jest znalezienie hasła zlokalizowanego gdzieś na serwerze w pliku, który spełnia warunki:
- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

1. Sprawdzam bierzącą ścieżkę `ls -la`
2. Katalog jest pusty, więc wychodzę `cd ..`
3. Układam komendę `find . -type f -size 33c -user bandit7 -group bandit6`
4. Do wszystkich plików nie mam dostępu, więc wychodzę do root `cd ..`
5. Używam jeszcze raz `find . -type f -size 33c -user bandit7 -group bandit6`
6. Wyników jes bardzo dużo, więc muszę jakoś odfiltrować te z "Permission denied"
7. Używam `grep` używając inwersji `-v` przekierowując błędy do stdout `2>$1`
8. Finalna komenda: `find . -type f -size 33c -user bandit7 -group bandit6 2>&1 | grep -v "Permission denied"`
9. Otwieram pasujący plik i zapisuję hasło

PS: zamiast użycia `grep` można też odfiltrować błędy odsyłając cały kanał stderr do null
`find . -type f -size 33c -user bandit7 -group bandit6 2>/dev/null`
Podobno jest to bardziej eleganckie i bardziej wydajne