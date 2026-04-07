Link: [Level 13](https://overthewire.org/wargames/bandit/bandit13.html)

Zadaniem jest znalezienie hasła w pliku `data.txt`, który jest hexdumpem pliku który został wielokrotnie skompresowany.

1. Sprawdzam zawartość pliku data.txt, jes to rzeczywiście hexdump
2. Szukam odpowiedniego narzędzia do odwrócenia procesu
3. Używam `xxd -r data.txt > unhexed` by utworzyć nowy plik z wynikiem
4. sprawdzam typ pliku, jest to archiwum gz
5. próbuję `gzip -d unhexed`, niestety bez skutku
6. zmieniam nazwę pliku `mv unhexed unhexed.gz`
7. ponawiam `gzip -d unhexed.gz`
8. otrzymuję plik `unhexed`
9. sprawdzam jego typ, tym razem to archiwum bzip2
10. kilkukrotnie powtarzam rozpakowywanie kolejnych, zagnieżdżonych archiw aż otrzymuję plik `ASCII text`
11. Odczytuję i zapisuję hasło