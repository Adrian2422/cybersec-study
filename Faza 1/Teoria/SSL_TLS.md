SSL (Secure Sockets Layer), a po nim jego następca TLS (Transport Layer Security) to protokoły pozwalające na nawiązywanie szyfrowanych połączeń, które mają zapobiec przejęciu danych przez osoby trzecie.

Normalnie [[HTTP]] to jak zwyczajna, prosta koperta - każdym może ją otworzyć, przeczytać zawartość i ponownie zakleić a nadawca i odbiorca nigdy się o tym nie dowiedzą.

Kiedy wpisujesz `https://` w przeglądarce (albo używasz innych narzędzi takich jak `openssl s_client)`, Twój komputer i serwer przeprowadzają tzw. **TLS Handshake**. Ten "uścisk dłoni" ma trzy cele: uwierzytelnienie serwera, ustalenie wspólnego klucza szyfrowania i uruchomienie bezpiecznego kanału.

![[Pasted image 20260407113100.png]]Krok który jest tu kluczowy, to moment wymiany kluczy. Serwer ma parę kluczy: klucz publiczny i klucz prywatny. Przeglądarka pobiera klucz publiczny z certyfikatu, szyfruje nim tajny sekret i wysyła. Serwer jako jedyny może to odszyfrować. Teraz obie strony generują z tego sekretu identyczny klucz sesji, którym od tej pory szyfrują cały ruch - i to już szyfrowanie symetryczne, bo jest dużo szybsze.

## Certyfikat - skąd wiemy, że serwer jest tym, za kogo się podaje?
Tu wchodzi pojęcie **Certificate Authority** (CA). To zaufana trzecia strona (np. Let's Encrypty, DigiCert, Sectigo), która podpisuje certyfikaty cyfrowo, zaświadczając: "Tak, ten certyfikat naprawdę należy do bank.pl". Twoja przeglądarka ma wbudowaną listę zaufanych CA. Kiedy serwer pokazuje certyfikat, przeglądarka sprawdza, czy ktoś z tej listy go podpisał.

Stąd bierze się ta kłódka w pasku adresu. Kiedy jej brakuje albo certyfikat jest przeterminowany, przeglądarka wyświetla ostrzeżenie - bo nie może zweryfikować tożsamości serwera.