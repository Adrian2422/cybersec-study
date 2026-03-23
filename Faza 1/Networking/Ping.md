Jest to jedno z podstawowych narzędzi używanych w sieciach. Ping stosuje pakiety **ICMP** (**I**nternet **C**ontrol **M**essage **P**rotocol) by badać stan połączeń pomiędzy urządzeniami (jego szybkość i "zdrowie"). 

Przykład:
```powershell
> ping 8.8.8.8

Pinging 8.8.8.8 with 32 bytes of data:
Reply from 8.8.8.8: bytes=32 time=5ms TTL=116
Reply from 8.8.8.8: bytes=32 time=5ms TTL=116
Reply from 8.8.8.8: bytes=32 time=5ms TTL=116
Reply from 8.8.8.8: bytes=32 time=5ms TTL=116

Ping statistics for 8.8.8.8:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 5ms, Maximum = 5ms, Average = 5ms
```

