Link: [Level 17](https://overthewire.org/wargames/bandit/bandit17.html)

1. Mapuję porty `nmap localhost`
2. Na liście nie pojawia się zakres 31000-32000, więc stosuję flagi `-p31000-32000 -A`
3. Pojawia się szczegółowa lista zakresu portów
4. Wnioskując po kolumnie SERVICE dwa porty obsługują ssl, ale jeden to `echo` a drugi `unknown`
5. Zgaduję, że `echo` po prostu zwraca input więc sprawdzam ten drugi `openssl s_client -connect localhost:31790 -nocommands`
6. Otrzymuję klucz prywatny, prawdopodobnie do kolejnego levelu