Link: [Level 6](https://overthewire.org/wargames/bandit/bandit6.html)

Zadaniem jest znalezienie hasła zlokalizowanego w katalogu `inhere` w pliku, który spełnia warunki:
- human-readable
- 1033 bytes in size
- not executable

1. Już po samej liście warunków domyślam się, że że użycie `ls -la` albo `find .` będzie błędem, bo plików będzie bardzo dużo więc od razu zaczynam ograniczać komendę
2. Dodaję `-type f` by sprawdzać tylko pliki
3. Dodaję `! -executable` by wykluczyć  - nomen omen - executable
4. Nie ma flagi do sprawdzania typu pliku ale jest `grep` więc dorzucam ` | grep "ASCII text"`
5. Na koniec dorzucam przed pipe akcję `-exec file {} +`
6. Finalna komenda: `find -type f -size 1033c ! -executable -exec file {} + | grep "ASCII text"`
7. Otrzymuję jeden plik spełniający założenia, odczytuję go

PS: Po fakcie pomyślałem, że samo `cat` też można by dodać do komendy ale wymagałoby to zabezpieczeń przed wieloma plikami, białymi znakami itd. np:
`find . -type f -size 1033c ! -executable -exec file {} + | grep "ASCII text" | cut -d: -f1 | while read -r line; do cat "$line"; done`