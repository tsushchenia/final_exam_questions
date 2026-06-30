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

![Nawiązywanie połączenia](<[[https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Tcp_normal.svg/2560px-Tcp_normal.svg.png](https://soisk.info/images/thumb/8/8c/Tcp_normal.png/300px-Tcp_normal.png)](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Tcp_normal.svg/250px-Tcp_normal.svg.png)>)

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


## 12. Porównanie modelu OSI i TCP/IP

### Model OSI

**Model OSI** — model warstwowy, który opisuje komunikację w sieciach komputerowych. Składa się z 7 warstw, które są zorganizowane w stos. Każda warstwa odpowiada za inne zadania. Każda warstwa komunikuje się tylko z warstwami sąsiadującymi. Każda warstwa ma swoje własne protokoły. Model OSI jest modelem teoretycznym, który nie jest stosowany w praktyce.

![Model OSI](<https://upload.wikimedia.org/wikipedia/commons/thumb/2/2b/Osi-model.png/2560px-Osi-model.png>)

![Model2](https://upload.wikimedia.org/wikipedia/commons/thumb/5/56/Kapsu%C5%82kowanie_danych_wg_modelu_odniesienia_OSI.svg/1280px-Kapsu%C5%82kowanie_danych_wg_modelu_odniesienia_OSI.svg.png)

Warstwy modelu OSI:

1. **fizyczna** — określa sposób transmisji danych (np. przewody, światłowody, fale radiowe)
2. **łącza danych** —  operuje na ramkach danych, które są przesyłane między węzłami sieci. Używa adresów MAC. Zapewnia kontrolę błędów i przepływ danych. Urządzeniem tej warstwy jest bridge i switch. Ma dwie podwarstwy:
   1. **MAC** — określa sposób dostępu do medium transmisyjnego (np. CSMA/CD) (niższa)
   2. **LLC** — określa sposób przesyłania danych (np. LLC1, LLC2) (wyższa)
3. **sieciowa** — określa sposób przesyłania pakietów między węzłami sieci. Używa adresów IP. Zapewnia trasowanie i adresowanie. Protokoły: IP, ICMP, ARP. Urządzeniem tej warstwy jest router.
4. **transportowa** — zapewnia całościowe połączenie, składa dane w strumień. Używa portów. Zapewnia kontrolę przepływu i błędów. Protokoły: TCP, UDP.
5. **sesji** — określa sposób nawiązywania, utrzymywania i zrywania sesji między aplikacjami. Synchronizuje różne aplikacje. Protokoły: NetBIOS, SAP, PPTP, SOCKS, L2TP.
6. **prezentacji** — określa sposób reprezentacji danych, przetwarza dane do postaci kanonicznej (gdy przetwarza w dół stosu). Odpowiada za kodowanie i konwersję danych. Obsługuje także rzeczy MPEG, JPG, GIF. Protokoły: MIME.
7. **aplikacji** — zajmuje się specyfikacją interfejsu, który wykorzystują aplikacje do przesyłania danych do sieci. Protokoły: HTTP, Telnet, NFS, POP3, SSH.

Warstwy 5-7 są warstwami **usługowymi**.

### TCP/IP

**TCP/IP** — model warstwowy, który opisuje komunikację w sieciach komputerowych. Składa się z 4 warstw, które są zorganizowane w stos. Każda warstwa odpowiada za inne zadania. Każda warstwa komunikuje się tylko z warstwami sąsiadującymi. Każda warstwa ma swoje własne protokoły. Model TCP/IP jest modelem praktycznym, który jest stosowany w praktyce. Każdy nowoczesny system operacyjny implementuje model TCP/IP.

![Model TCP/IP](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/UDP_encapsulation.svg/1280px-UDP_encapsulation.svg.png)

1. **dostępu do sieci/fizyczna** — określa sposób transmisji danych (np. przewody, światłowody, fale radiowe) i połączenia między urządzeniami. MAC
2. **internetowa** — określa sposób przesyłania pakietów między węzłami sieci. Używa adresów IP. Zapewnia trasowanie i adresowanie. Protokoły: IP, ICMP, ARP. Urządzeniem tej warstwy jest router.
3. **transportowa** — zapewnia całościowe połączenie, składa dane w strumień. Używa portów. Zapewnia kontrolę przepływu i błędów. Protokoły: TCP, UDP.
4. **aplikacji** — użyteczne dla człowieka aplikacje


## 15. Hermetyzacja, dziedziczenie i polimorfizm w programowaniu obiektowym

### Hermetyzacja

**Hermetyzacja** — ukrywanie szczegółów implementacji. W programowaniu obiektowym hermetyzacja jest realizowana przez ukrywanie atrybutów klasy (np. poprzez ustawienie ich jako prywatne) i udostępnianie ich za pomocą metod (np. getterów i setterów).

# Programowanie obiektowe

[`back to README.md`](../README.md)

## 14. Obiekt i klasa w wybranym języku programowania zorientowanym obiektowo

> **Obiekt** to instancja klasy. **Klasa** to szablon, na podstawie którego tworzone są obiekty.

### Klasa

**Klasa** — częściowa lub całkowita definicja dla obiektów, które będą tworzone na jej podstawie. Klasa posiadają strukturę (**atrybuty**/pola) jak i interfejs — sposób komunikacji z obiektami danej klasy (**metody**) które będą tworzone na jej podstawie. Klasy zazwyczaj są *typami* języka programowania

#### Przykład w Javie

```java
public class Person {
    // ATRYBUTY
    private String name;
    private int age;
    
    // KONSTRUKTOR
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    // METODY
    // GETTERY (akcesory)
    public String getName() {
        return name;
    }
    
    public int getAge() {
        return age;
    }
    // SETTERY (mutator)
    public void setName(String name) {
        this.name = name;
    }
    
    public void setAge(int age) {
        this.age = age;
    }
    // INNE METODY
    public void introduce() {
        System.out.println("Hi, my name is " + name + " and I am " + age + " years old.");
    }
}
```

Rodzaje klas:

* **Klasa abstrakcyjna** — klasa, która nie może być instancjonowana, służy jako szablon dla innych klas
* **Klasa finalna** — klasa, która nie może być rozszerzona (dziedziczona)
* **Klasa anonimowa** — klasa, która nie posiada nazwy, jest tworzona w miejscu użycia
* **Klasa wewnętrzna/zagnieżdżona** — klasa zdefiniowana wewnątrz innej klasy
* **Klasa lokalna** — klasa zdefiniowana wewnątrz metody/innego bloku kodu
* **Meta-klasa** — klasa, której obiekty są klasami
* **Klasa wirutalna** — klasa, której obiekty są obiektami innych klas

### Obiekt

**Obiekt** — instancja klasy. Obiekt posiada stan (wartości atrybutów) oraz zachowanie (metody). Obiekt jest tworzony na podstawie klasy. Obiekt jest *wartością* języka programowania. Ma też swoją *tożsamość* (cechę odróżniającą go od innych obiektów, np id).

## 15. Hermetyzacja, dziedziczenie i polimorfizm w programowaniu obiektowym

### Hermetyzacja

**Hermetyzacja** — ukrywanie szczegółów implementacji. W programowaniu obiektowym hermetyzacja jest realizowana przez ukrywanie atrybutów klasy (np. poprzez ustawienie ich jako prywatne) i udostępnianie ich za pomocą metod (np. getterów i setterów).

### Dziedziczenie

**Dziedziczenie** — mechanizm, który pozwala na tworzenie nowych klas na podstawie już istniejących.
Klasa, która jest podstawą do stworzenia nowej klasy nazywamy **klasą bazową**.
Klasa, która jest tworzona na podstawie klasy bazowej nazywamy **klasą pochodną**.
Klasa pochodna dziedziczy po klasie bazowej jej atrybuty i metody (nie ma dostępu do zmiennych i metod prywatnych klasy bazowej w Javie).
Klasa pochodna może rozszerzać funkcjonalność klasy bazowej poprzez dodanie nowych atrybutów i metod.
Klasa pochodna może nadpisywać metody klasy bazowej.
Klasa pochodna może być bazą dla kolejnej klasy pochodnej. Dziedziczenie jest realizowane przez słowo kluczowe `extends`.

Mechanizm dziedziczenia pozwala na tworzenie hierarchii klas, które są ze sobą powiązane. Klasa pochodna jest bardziej wyspecjalizowana niż klasa bazowa.

### Polimorfizm

**Polimorfizm** — mechanizm, który pozwala na wykonywanie tej samej operacji na różnych typach danych. Polimorfizm jest realizowany przez przeciążanie metod i operatorów oraz przez dziedziczenie. Polimorfizm pozwala na traktowanie obiektów różnych klas w ten sam sposób. Na przykład jeśli klasa `Pies` dziedziczy po klasie `Zwierzę` to obiekt klasy `Pies` może być traktowany jako obiekt klasy `Zwierzę`.

Przykład w Javie:

```java
public class Animal {
    public void makeSound() {
        System.out.println("Animal sound");
    }
}

public class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Woof");
    }
}

public class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Meow");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Animal();
        Animal dog = new Dog();
        Animal cat = new Cat();
        
        animal.makeSound(); // Animal sound
        dog.makeSound(); // Woof
        cat.makeSound(); // Meow
    }
}
```

* **Polimorfizm ad hoc** — polimorfizm, który jest realizowany przez przeciążanie metod i operatorów
* **Polimorfizm uniwersalny** — polimorfizm, który jest realizowany przez dziedziczenie

* **Polimorfizm statyczny** — polimorfizm, który jest realizowany w czasie kompilacji. Przykładem jest przeciążanie operatorów
* **Polimorfizm dynamiczny** — polimorfizm, który jest realizowany w czasie wykonania. Przykładem jest metody wirtualne — konkretna metoda jest wybierana w czasie wykonania w zależności od typu obiektu


# 18. Algorytmy sortowania.

## Definicje

**************************************Warunek stabilności************************************** — zachowanie początkowego ustawienia względem siebie elementów równych (rekordów o takich samych kluczach).

**************************************Operacja dominująca************************************** — porównanie elementów w ciągu.

************************************************************************Złożoność pamięciowa alg. sortowania************************************************************************ — ilość dodatkowej pamięci (oprócz n-miejsc pamięci dla elementów ciągu) potrzebnej do wykonania algorytmu.

## Typy algorytmów sortowania

### Sortowanie przez porównywanie elementów

- sortowanie przez selekcję (selection sort)
- sortowanie przez wstawianie (insertion sort)
- sortowanie bąbelkowe (bubble sort)
- sortowanie koktajlowe (cocktail sort)
- sortowanie Shella i Grzebieniowe (Shell and Comb sort)

### Sortowanie metodą dziel i zwyciężaj

- sortowanie przez scalanie (merge sort)
- sortowanie sybkie (quick sort)

### Inne

- sortowanie przez zliczanie (counting sort)
- sortowanie przez kopcowanie (heap sort)
- sortowanie pozycyjne (radix sort)

## Podział względem stabilności

### Algorytmy sortowania stabilnego

- przez wstawianie
- bąbelkowe
- koktajlowe
- pozycyjne
- przez scalanie
- przez zliczanie

### Algorytmy sortowania niestabilnego

- przez selekcję

### Definicje

************Strukturą danych************ nazywamy sposób uporządkowania przechowywanych na komputerze danych.

********************Abstrakcyjnym typem danych******************** nazywamy formalną specyfikację przechowywania obiektów oraz zbiór dobrze opisanych operacji na tych obiektach.

<!-- <aside> -->
> 💡 Struktura danych jest implementacją konkretnej abstrakcyjnej struktury danych.

<!-- </aside> -->

### Przykłady stuktur

- Liniowe abstrakcyjne struktury danych
    - Stos
    - Kolejka
    - Listy (jedno/dwukierunkowe, cykliczne/niecykliczne)
- Tablice haszujące
- Drzewiaste struktury danych
    - Drzewa poszukiwań binarnych (binary search trees)
    - Koce
    - Drzewa AVL
    - Drzewa Czerwono-Czarne
- Grafy
# 18. Algorytmy sortowania.

## Definicje

**************************************Warunek stabilności************************************** — zachowanie początkowego ustawienia względem siebie elementów równych (rekordów o takich samych kluczach).

**************************************Operacja dominująca************************************** — porównanie elementów w ciągu.

************************************************************************Złożoność pamięciowa alg. sortowania************************************************************************ — ilość dodatkowej pamięci (oprócz n-miejsc pamięci dla elementów ciągu) potrzebnej do wykonania algorytmu.

## Typy algorytmów sortowania

### Sortowanie przez porównywanie elementów

- sortowanie przez selekcję (selection sort)
- sortowanie przez wstawianie (insertion sort)
- sortowanie bąbelkowe (bubble sort)
- sortowanie koktajlowe (cocktail sort)
- sortowanie Shella i Grzebieniowe (Shell and Comb sort)

### Sortowanie metodą dziel i zwyciężaj

- sortowanie przez scalanie (merge sort)
- sortowanie sybkie (quick sort)

### Inne

- sortowanie przez zliczanie (counting sort)
- sortowanie przez kopcowanie (heap sort)
- sortowanie pozycyjne (radix sort)

## Podział względem stabilności

### Algorytmy sortowania stabilnego

- przez wstawianie
- bąbelkowe
- koktajlowe
- pozycyjne
- przez scalanie
- przez zliczanie

### Algorytmy sortowania niestabilnego

- przez selekcję
- szybkie
- przez kopcowanie

## Sortowanie Bąbelkowe

### Zasada działania

1. Porównujemy kolejne pary sąsiadujących elementów n-elementowej tablicy.
2. Jeżeli nie są właściwie uporządkowane, zamieniamy je miejscami.
3. Powtarzamy procedurę n-razy za każdym razem przeglądając o jeden element mniej.

![Bubble-sort-example-300px.gif](../src/img/algorytmy/Bubble-sort-example-300px.gif)

<!-- <aside> -->
> 💡 W i-tym przebiegu wyznaczamy i-ty najmniejszy/największy element zbioru oraz umieszczany jest na właściwej pozycji

<!-- </aside> -->

### Złożoność czasowa: O(N^2)

### Możliwe ulepszenia

- zapamiętywanie czy w trakcie przejścia dokonano zmian - jeżeli nie, algorytm kończy działanie
- zapamiętywanie pozycji ostatniej zmiany — wszystkie pary obiektów sąsiadujących powyżej (poniżej) tej pozycji, są już ustawione w odpowiedniej kolejności.

## Sortowanie koktailowe

Jest do ********************************************************************dwukierunkowe sortowanie bąbelkowe******************************************************************** — wersja bubble sorta, w której przejścia po tablicy odbywają się ze zmiennym kierunkiem (raz od prawej - malejąco, a potem od lewej - rosnąco).

Typowa złożoność czasowa jest klasy O(n^2), dla zbiorów w znacznym stopniu posortowanych, złożoność redukuje się do O(n).

## Sortowanie przez wstawianie (Insertion sort)

### Zasada działania

1. Elementy tablicy podzielone (umownie) na ciąg wynikowy i źródłowy.
2. W kroku **i** (począwszy od i = 2) posortowanych jest i-1 elementów tablicy, a element i-ty zostaje pomiędzy nie w miejsce, które zachowuje posortowanie ciągu.
3. W celu znalezienia odpowiedniego miejsca należy przeglądać posortowaną część tablicy, o ile to możliwe od razu przesuwając je i tworząc miejsce na nowy element.

### Złożoność czasowa: O(n^2)

### Możliwe ulepszenia

Ciąg wynikowy jest już uporządkowany — można zastosować metodę **przeszukiwania połówkowego (binary serach)**, w celu ustalenia miejsca wstawienia nowego obiektu.

Ulepszenie to zmniejsza tylko liczbę porównań, a nie liczbę potrzebnych przesunięć.

## Shell Sort - sortowanie metodą malejących przyrostów

### Zasada działania

1. Sortowany zbiór podziel na podzbiory, których elementy są odległe od siebie w sortowanym zbiorze o pewien odstęp h.
2. Każdy z tych podzbiorów posortuj algorytmem przez wstawianie.
3. Następnie odstęp zmniejsz, co powoduje powstanie nowych podzbiorów (będzie ich już mniej)
4. Sortowanie powtórz i zmniejsz odstęp, aż osiągnie on wartość 1. Wtedy cały zbiór sortujemy typowym Insertion Sortem.

<!-- <aside> -->
> 💡 Dzięki początkowym, dużym odstępom, elementy były przesuwane w zbiorze bardziej efektywnie - na duże odległości.

<!-- </aside> -->

### Złożoność czasowa

Shell Sort jest to najlepszy pod względem szybkości czasu wykonania algorytm sortujący w klasie ************O(n^2)************

## Sortowanie przez wybieranie (Selection sort)

### Zasada działania

1. W pierwszym kroku algorytmu znajduje największy element tablicy i zamienia go z ostatnim elementem.
- szybkie
- przez kopcowanie

## Sortowanie Bąbelkowe

### Zasada działania

1. Porównujemy kolejne pary sąsiadujących elementów n-elementowej tablicy.
2. Jeżeli nie są właściwie uporządkowane, zamieniamy je miejscami.
3. Powtarzamy procedurę n-razy za każdym razem przeglądając o jeden element mniej.

![Bubble-sort-example-300px.gif](../src/img/algorytmy/Bubble-sort-example-300px.gif)

<!-- <aside> -->
> 💡 W i-tym przebiegu wyznaczamy i-ty najmniejszy/największy element zbioru oraz umieszczany jest na właściwej pozycji

<!-- </aside> -->

### Złożoność czasowa: O(N^2)

### Możliwe ulepszenia

- zapamiętywanie czy w trakcie przejścia dokonano zmian - jeżeli nie, algorytm kończy działanie
- zapamiętywanie pozycji ostatniej zmiany — wszystkie pary obiektów sąsiadujących powyżej (poniżej) tej pozycji, są już ustawione w odpowiedniej kolejności.

## Sortowanie koktailowe

Jest do ********************************************************************dwukierunkowe sortowanie bąbelkowe******************************************************************** — wersja bubble sorta, w której przejścia po tablicy odbywają się ze zmiennym kierunkiem (raz od prawej - malejąco, a potem od lewej - rosnąco).

Typowa złożoność czasowa jest klasy O(n^2), dla zbiorów w znacznym stopniu posortowanych, złożoność redukuje się do O(n).

## Sortowanie przez wstawianie (Insertion sort)

### Zasada działania

1. Elementy tablicy podzielone (umownie) na ciąg wynikowy i źródłowy.
2. W kroku **i** (począwszy od i = 2) posortowanych jest i-1 elementów tablicy, a element i-ty zostaje pomiędzy nie w miejsce, które zachowuje posortowanie ciągu.
3. W celu znalezienia odpowiedniego miejsca należy przeglądać posortowaną część tablicy, o ile to możliwe od razu przesuwając je i tworząc miejsce na nowy element.

### Złożoność czasowa: O(n^2)

### Możliwe ulepszenia

Ciąg wynikowy jest już uporządkowany — można zastosować metodę **przeszukiwania połówkowego (binary serach)**, w celu ustalenia miejsca wstawienia nowego obiektu.

Ulepszenie to zmniejsza tylko liczbę porównań, a nie liczbę potrzebnych przesunięć.

## Shell Sort - sortowanie metodą malejących przyrostów

### Zasada działania

1. Sortowany zbiór podziel na podzbiory, których elementy są odległe od siebie w sortowanym zbiorze o pewien odstęp h.
2. Każdy z tych podzbiorów posortuj algorytmem przez wstawianie.
3. Następnie odstęp zmniejsz, co powoduje powstanie nowych podzbiorów (będzie ich już mniej)
4. Sortowanie powtórz i zmniejsz odstęp, aż osiągnie on wartość 1. Wtedy cały zbiór sortujemy typowym Insertion Sortem.

<!-- <aside> -->
> 💡 Dzięki początkowym, dużym odstępom, elementy były przesuwane w zbiorze bardziej efektywnie - na duże odległości.

<!-- </aside> -->

### Złożoność czasowa

Shell Sort jest to najlepszy pod względem szybkości czasu wykonania algorytm sortujący w klasie ************O(n^2)************

## Sortowanie przez wybieranie (Selection sort)

### Zasada działania

1. W pierwszym kroku algorytmu znajduje największy element tablicy i zamienia go z ostatnim elementem.
2. W i-tym kroku sortowania n-elementowej tablicy algorytm znajduje największy element spośród pierwszych (n-i+1) elementów (nieposortowana część ciągu) i zamienia go miejscami (n-i+1) elementem tablicy (ostatnim w nieposortowanej części ciągu).
3. Sortowanie odbywa się w n-1 przebiegach.

### Złożoność czasowa

Czas pracy algorytmu jest niezależny od rodzaju danych wejściowych - złożoność ************O(n^2)************, nawet jeżeli tablica wejściowa jest posortowana.





