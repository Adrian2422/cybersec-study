Sieć LAN to sieć komputerowa obejmująca ograniczony obszar geograficzny, przykładowo jeden budyne, pietro.

Urządzenia w tej sieci komunikują się ze sobą bezpośrednio w standardzie Ethernet (IEEE 802.3) lub Wi-Fi (IEEE 802.11). Urządzenia identyfikują się poprzez [[Adres MAC]] na poziomie warstwy drugiej **modelu OSI** a pomiędzy podsieciami używają prywatnych adresów IP.

Centralnym urządzeniem sieci LAN jest **switch** (przełącznik) który zapamiętuje adresy MAC podłączonych urządzeń w tablicy **CAM** (**C**ontent **A**ddressable **M**emory) i przesyła ramki Ethernet precyzyjnie do konkretnego portu

LAN jest często celem ataków typu **ARP spoffing**, czyli podszywania się pod inne urządzenia żeby przechwycić ich komunikację.

Przykładowy rekonesans:
`nmap -sn 192.168.1.0/24`
To polecenie skanuje całą podsieć (wszystkie adresy od `192.168.1.1` do `192.168.1.254`) i zwraca listę aktywnych urządzeń. Zapis `/24` to tzw. **maska podsieci** w notacji CIDR — oznacza, że pierwsze 24 bity adresu są częścią sieci, a pozostałe 8 bitów identyfikuje konkretne urządzenie. Właśnie tak pentesterzy robią pierwsze rozpoznanie po wejściu do sieci.