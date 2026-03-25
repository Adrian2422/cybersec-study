Link: [Level 8](https://overthewire.org/wargames/bandit/bandit8.html)

Zadaniem jest znalezienie hasła zlokalizowanego w pliku `data.txt` tuż po słowie `millionth`

1. Sprawdzam katalog `ls -la`
2. Zadanie sugeruje, że plik jest duży więc zamiast `cat` używam `less`
3. Przypuszczenia się potwierdzają, musimy więc jakoś znaleźć linię w postaci `millionth {pass}`
4. Oczywistym wyborem jest `grep` więc podaję komendę `grep milionth data.txt`
5. Otrzymałem jedną linię, zapisuję hasło