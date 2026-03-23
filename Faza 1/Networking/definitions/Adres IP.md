**I**nternet **P**rotocol Address służy do identyfikowania hosta w sieci przez określony czas, przy czym ten sam adres może zostać później przypisany do innego urządzenia.

Adres IP ma następującą strukturę:
192.168.1.1

Jest to zestaw liczb podzielony na cztery [[Oktet]]y. Suma wartości poszczególnych bajtów da w wyniku adres IP urządzenia w sieci.
Liczba ta jest obliczana techniką "IP addressing & subnetting".

Adres IP może zmienić urządzenie ale nie może być zduplikowany w tej samej sieci.

Adres IP przestrzega pewnych  standardów zwanych protokołami. Protokołem nazywamy zestaw zasad które wymuszają na urządzeniach komunikację we wspólnym języku.

Urządzenia mogą być jednocześnie w sieci prywatnej oraz publicznej i posiadać dla nich osobne adresy IP (public i private).

Przykład:

| Device name   | Ip Address   | Ip Address Type |
| ------------- | ------------ | --------------- |
| DESKTOP-AKW11 | 192.168.1.77 | Private         |
| DESKTOP-AKW11 | 86.157.52.21 | Public          |
| DESKTOP-PBY25 | 192.168.1.74 | Private         |
| DESKTOP-PBY25 | 86.157.52.21 | Public          |
Oba urządzenia należą do tej samej sieci i wysyłane przez nie data będą identyfikowane przez ten sam adres publiczny 86.157.52.2. Jednak wewnątrz tej sieci mają swoje własne, prywatne adresy które pozwalają je precyzyjnie zidentyfikować.
Publiczne adresy IP są nadawane przez **I**nternet **S**ervice **P**rovider (ISP) czyli dostawcę internetu (Plus, Play etc.)

Powyższe adresy IP są zapisane w wersji 4 (IPv4) która ma swoją wadę: jest relatywnie mało pojemna ("tylko" $2^{32}$ miliarda adresów).
IPv6 jest kolejną iteracją adresu IP która ma zaadresować ten problem. Jej pojemność to $2^{128}$ więc jest w stanie przydzielić znacznie, znacznie więcej adresów.

Przykład: 2001:db8:85a3::8a2e:370:7334