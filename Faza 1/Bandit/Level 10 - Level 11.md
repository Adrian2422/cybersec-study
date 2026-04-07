Link: [Level 11](https://overthewire.org/wargames/bandit/bandit11.html)

Zadaniem jest znalezienie hasła w pliku `data.txt` które zawiera dane zakodowane jako base64

1. Listuję katalog `ls`
2. Sprawdzam plik `file data.txt`
3. Jest to plik tekstowy więc w środku zapewne jest po prostu hash base64
4. Sprawdzam manual `man base64`
5. Dekoduję plik `base64 -d data.txt`
6. Zapisuję otrzymane hasło