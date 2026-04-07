Link: [Level 16](https://overthewire.org/wargames/bandit/bandit16.html)

Hasło do bandit16 może być otrzymane przez wysłanie obecnego hasła na port localhost:30001 z użyciem SSL/TLS.

1. Przeglądam listę przydatnych komend w poszukiwaniu takiej, która pomoże mi nawiązać połączenie SSL.
2. `man openssl` a konkretnie `s_client` wydaje się być idealnym rozwiązaniem
3. Sprawdzam `man openssl-s_client`
4. Używam `openssl s_client -connect localhost:30001`
5. Wpisuję hasło