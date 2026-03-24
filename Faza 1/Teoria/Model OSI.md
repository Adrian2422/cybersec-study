Model OSI (**O**pen **S**ystems **I**nterconnection) to pewnego rodzaju umowa pomiędzy inżynierami z całego świata: ustalamy razem, że komunikacja sieciowa będzie podzielona na 7 warstw, każda z jasno określonymi zadaniami. Dzięki temu firma A może produkować karty sieciowe, firma B pisać protokół transportowy a firma C budować aplikację - i wszystko ze sobą będzie działać, bo każdy wie, co do niego należy.

Na przykładzie wiadomości email: w momencie kliknięcia "Wyślij" dane zaczynają podróż w dół wszystkich 7 warstw. Każda warstwa dokłada do pakietu swój nagłówek i instrukcje - proces ten nazwany jest **enkapsulacją**. Po drugiej stronie, odbiorca przechodzi przez wszystkie warstwy do góry, rozpakowując ramkę z kolejnych nagłówków - inaczej **dekapsulacja**.

![[osi.png]]

Warstwa fizyczna to czyste dane - impulsy elektryczne, światło w światłowodzie, fale radiowe w WiFi. Definiuje jak bit jest zamieniany na coś, co może podróżować przez medium transmisyjne.
Urządzenia w tej warstwie to (historycznie) huby, reapeatery i wszelkie kable.
W tej warstwie dzieją się ataki typu "war driving", podsłuchy poprzez fizyczny dostęp do komputera i wpięcie do portu itd.

Warstwa łącza danych dodaje adresy MAC ([[Adres MAC]]). Tutaj operuje protokół Ethernet a switch decyduje, do którego portu przekierować ramkę.
Mechanizm **[[CRC]]** (**C**yclic **R**edundancy **C**heck) to suma kontrolka dołączana do każdej ramki, dzięki której odbiorca może sprawdzić, czy dane nie zostały uszkodzone po drodze.
Tutaj pojawiają się ataki typu "ARP Spoofing", atakujący wysyła fałszywe odpowiedzi ARP, przekonując urządzenia w sieci, że jego MAC to MAC routera. W efekcie cały ruch sieciowy przepływa przez maszynę atakującego (Man-in-the-middle).

Warstwa sieciowa wprowadza adresy IP i pojawia się pojęcie routowania, czyli znajdowanie drogi pakietu między różnymi sieciami. Protokół IP nadaje każdemu urządzeniu adres. Router - urządzenie  łączące różne sieci - czyta adres IP docelowy z pakietu  i decyduje, którą drogą go wysłać, korzystając z tablic routingu.
Tutaj operuje ICMP z którego korzystają [[Ping]] oraz Traceroute.
[[IP Spoofing]] to technika używana w atakach [[DDoS]]. Atakujący wysyła pakiety z podrobionym adresem IP ofiary do wielu serwerów - te odpowiadają na adres ofiary zalewając ją ruchem, którego nie zamawiała. Skanowanie portów za pomocą **nmap** też zaczyna się tutaj.

Warstwa transportowa odpowiada za protokół, jakim ramka zostanie wysłana dalej. Przykładowo [[TCP]] dba o to, by wszystkie pakiety dotarły i były w odpowiedniej kolejności (coś w rodzaju kuriera z potwierdzeniem odbioru).
[[UDP]] natomiast robi to szybciej ale bez gwarancji dostarczenia - idealny do streamowania wideo czy gier online, gdzie liczy się prędkość.
Porty to też warstwa 4. Port to liczba od 0 do 65535 wskazująca, który program ma obsłużyć dane.
Port 80 to HTTP, 443 to HTTPS, 22 to SSH, 25 to SMTP. Dzięki portom jeden komputer może jednocześnie serwować stronę, obsługiwać SSH i wysyłać maile.
[[SYN Flood]] to atak, gdzie atakujący wysyła tysiące pakietów SYN, nie kończąc handshake'u Serwer rezerwuje zasoby dla każdego nieukończonego połączenia i w końcu się dusi.
Port scanning również ma miejsce tutaj, bo nmap może mapować też porty i ustalać jakie usługi są uruchomione na celu.

Warstwa sesji zarządza nawiązywaniem i kończeniem połączeń. 

Warstwa prezentacji zajmuje się formatowaniem i szyfrowaniem danych. [[TLS]], [[SSL]], [[HTTPS]] mieszkają właśnie tutaj.

Warstwa aplikacji 

Znajomość warstw jest kluczowa do zrozumienia i przeciwdziałania atakom. [[XSS]] i [[SQL Injection]] atakują warstwę 7. Man-in-the-Middle może działać na warstwie 2 (ARP spoofing) lub 3. DDoS atakuje warstwę 4 zalewając serwer milionami pakietów TCP. Wiedząc, na której warstwie działa atak, wiesz też, gdzie szukać obrony.