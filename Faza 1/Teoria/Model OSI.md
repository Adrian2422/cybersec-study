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

Warstwa sesji zarządza nawiązywaniem i kończeniem połączeń między dwoma aplikacjami. Protokoły takie jak [[NetBIOS]] czy [[RPC]] działają tutaj. [[WebSocket]] też operuje na poziomie sesji.
[[Session hijacking]] to atak polegający na kradzieży identyfikatora sesji (np. ciasteczka sesyjnego przeglądarki) i podszywanie się pod zalogowanego użytkownika. Jeśli serwer identyfikuje użytkownika tylko po tokenie sesji i ten token wycieknie, a takujący może przejąć konto bez znajomości hasła.

Warstwa prezentacji zajmuje się formatowaniem, kompresją i szyfrowaniem danych. [[TLS]], [[SSL]], [[HTTPS]] mieszkają właśnie tutaj.
TLS (ang. _Transport Layer Security_, bezpieczeństwo warstwy transportowej) — protokół, który stoi za HTTPS i tą małą kłódką w przeglądarce — formalnie należy do tej warstwy. TLS szyfruje dane zanim trafią do warstwy transportowej, używając algorytmów takich jak AES (ang. _Advanced Encryption Standard_, zaawansowany standard szyfrowania). Negocjuje też certyfikaty, weryfikując, czy serwer jest tym, za kogo się podaje.
Formaty jak JPEG, PNG, MP4, czy standardy kodowania tekstu jak UTF-8 i ASCII też mieszkają na tej warstwie — to tu dane są tłumaczone na format zrozumiały dla aplikacji.
BEAST, POODLE, Heartbleed — to głośne podatności (słabości) w implementacjach TLS i jego poprzednika SSL. Downgrade attack polega na zmuszeniu połączenia do użycia starszej, słabszej wersji protokołu. Dlatego konfiguracja serwera, która wyłącza stare wersje TLS (1.0, 1.1) i słabe szyfry, jest tak ważna.

Warstwa aplikacji to najwyższa warstwa, gdzie użytkownik styka się z siecią. Protokoły warstw aplikacji definiują język, jakim rozmawiają ze sobą aplikacje.
[[HTTP]] (ang. _HyperText Transfer Protocol_) to język przeglądarki i serwera WWW — żądania GET, POST, PUT, DELETE, nagłówki, kody odpowiedzi (200 OK, 404 Not Found, 500 Internal Server Error). HTTPS to HTTP + TLS z warstwy 6.
DNS (ang. _Domain Name System_) tłumaczy nazwy domenowe na adresy IP — kiedy piszesz `google.com`, zapytanie DNS leci do serwera nazw i wraca z adresem IP. Bez DNS Internet byłby siecią liczb, które nikt by nie pamiętał.
SMTP (ang. _Simple Mail Transfer Protocol_) wysyła maile, IMAP i POP3 je odbierają. FTP (ang. _File Transfer Protocol_) transferuje pliki. SSH (ang. _Secure Shell_, bezpieczna powłoka) daje szyfrowany dostęp do zdalnej linii komend.
[[SQL Injection]] i [[XSS]] (ang. _Cross-Site Scripting_, skryptowanie między witrynami) atakują aplikacje webowe przez HTTP. DNS poisoning (zatruwanie cache DNS) podmienia odpowiedzi DNS, kierując użytkowników na fałszywe strony. Phishing (wyłudzanie danych) operuje przez SMTP.

Znajomość warstw jest kluczowa do zrozumienia i przeciwdziałania atakom. Wiedząc, na której warstwie działa atak, wiesz też, gdzie szukać obrony.