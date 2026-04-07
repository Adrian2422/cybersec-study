Link: [Level 2](https://overthewire.org/wargames/bandit/bandit2.html)

Zadaniem jest znalezienie hasła zlokalizowanego w pliku `-`

1. Listuję katalog home `ls -la`.
2. Zwykłe użycie `cat -` nie działa (powershell używa `-` jako synonimu dla `stdin`), więc szukam wyjaśnienia i alternatywy.
3. Używam alternatyw:
	1. pełna ścieżka `cat ./-`
	2. narzędzie more `more -`
	3. przekierowanie `cat < -`
4. Odczytuję i zapisuję hasło