Link: [Level 15](https://overthewire.org/wargames/bandit/bandit15.html)

Zadaniem jest wysłanie aktualnego hasła na `localhost:30000`  by otrzymać hasło dla `bandit15`.

1. Przezornie mapuję porty `nmap localhost`
2. Widzę że port 30000 jest otwarty i obsługuje tcp
3. Otwieram połączenie telnet `telnet localhost 30000` i w prompt wpisuję obecne hasło
4. Otrzymuję hasło dla `bandit15`

PS: Przetestowałem również `nc localhost 30000` oraz `echo ... | nc localhost 30000`, zadziałały podobnie