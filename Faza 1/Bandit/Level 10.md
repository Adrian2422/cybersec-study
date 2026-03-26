Link: [Level 10](https://overthewire.org/wargames/bandit/bandit10.html)

Zadaniem jest znalezienie hasła w pliku `data.txt` które zaczyna się od kilku znaków `=`

1. Listuję katalog `ls -la`
2. sprawdzam typ pliku `file data.txt`
3. Jest to typ `data`, najpewniej binarka więc trzeba go traktować jak tekst
4. Używam `grep` z flagą `-a` by potraktować go jako text oraz flagą `-o` by wyświetlić tylko trafienia
5. Używam również regexp by trafić fragmenty zaczynające się od conajmniej dwóch znaków `=`
6. Finalna komenda: `grep -ao "=\{2,\}.*" data.txt` 