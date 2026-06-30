## 9. Protokoły TCP i UDP – porównanie i zastosowanie

### UDP

**UDP (User Datagram Protocol — *protokół pakietów użytkownika*)** — jeden z protokołów internetowych. Jest stosowany w **warstwie transportowej**. Jest to protokół bezpołączeniowy, więc nie ma narzutu na nawiązywanie połączenia i śledzenie sesji (w przeciwieństwie do TCP). Nie ma też mechanizmów kontroli przepływu i retransmisji.

Jest dzięki temu prostszy i szybszy od TCP, ale mniej niezawodny.

Najczęściej stosowany jest do przesyłania danych w czasie rzeczywistym, np. w transmisji strumieniowej (np. wideo, audio) czy do gier sieciowych. Korzysta z niego np. protokół DNS czy VoIP

UDP wspiera również **multicast** (wysyłanie do wielu odbiorców jednocześnie).

### TCP

**TCP (Transmission Control Protocol — *protokół kontroli transmisji*)** — jeden z protokołów internetowych. Jest stosowanym **warstwie transportowej**. Jest to protokół połączeniowy, więc wymaga nawiązania połączenia i śledzenia sesji (w przeciwieństwie do UDP). Ma też mechanizmy kontroli przepływu i retransmisji. Gwarantuje dostarczenie danych w kolejności, w jakiej zostały wysłane. Wszystkie dane muszą być dostarczone, a jeśli nie zostaną, to połączenie zostanie zerwane. Stosuje się tez sumy kontrolne (CRC) do sprawdzania poprawności danych i ich integralności. Stosuje się również potwierdzenia odbioru danych.

Jest to protokół *klient-serwer*

Jest dzięki temu bardziej niezawodny, ale mniej prosty i wolniejszy od UDP.

#### Nawiązywanie połączenia three-way handshake

1. Klient wysyła pakiet `SYN` do serwera
2. Serwer odpowiada pakietem `SYN-ACK`
3. Klient odpowiada pakietem `ACK`

![Nawiązywanie połączenia](<[https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Tcp_normal.svg/2560px-Tcp_normal.svg.png](https://soisk.info/images/thumb/8/8c/Tcp_normal.png/300px-Tcp_normal.png)>)

#### Zerwanie połączenia

1. Klient wysyła pakiet `FIN` do serwera
2. Serwer odpowiada pakietem `ACK`
3. Połączenie zostaje zamknięte

#### Stany połączenia

1. `CLOSED` — połączenie nie jest nawiązane
2. `LISTEN` — serwer nasłuchuje na połączenia przychodzące
3. `SYN-SENT` — klient wysłał pakiet `SYN`
4. `SYN-RECEIVED` — serwer wysłał pakiet `SYN-ACK`
5. `ESTABLISHED` — połączenie zostało nawiązane
6. `FIN-WAIT-1` — klient wysłał pakiet `FIN`
7. `FIN-WAIT-2` — serwer wysłał pakiet `ACK`
8. `CLOSE-WAIT` — serwer wysłał pakiet `FIN`
9. `LAST-ACK` — klient wysłał pakiet `ACK`
10. `TIME-WAIT` — połączenie zostało zamknięte
11. `CLOSING` — klient wysłał pakiet `FIN` i `ACK` jednocześnie

Oba protokoły są stosowane w **warstwie transportowej** modelu TCP/IP. Używają również portów, aby przekazać dane do odpowiednich aplikacji i identyfikować je.
