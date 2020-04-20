## System operacyjny w środowisku sieciowym

### Zadania


1. Z wykorzystaniem maszyny wirtualnej, zainstaluj SO oraz wypisz parametry konfiguracji IP tj:
   * Adres
   * Maska
   * Adres bramy
   * DNS 1
   * DNS 2
    
    Powyższe parametry uzyskaj na wszystkich z wymienionych systemów

   * [Linux Alpine](https://alpinelinux.org/)
    - miłam mega problemy z VirtualBoxem, wyskakiwały jakieś szalone błędy na które nie umiałam znaleźć nigdzie odpowiedzi. Po kilku godzinach szukania i główkowania udało się - satysfakcja jeszcze większa niż wredota błędu. Okazało się, że mój Alpine Linux stworzył się nie w tym pliku co trzeba (to był pierwszy "issue"), dodatkowo nie miałam możliwości wybrania 64-bitowego Linuxa (same opcje 32) - trzeba było kliknąć "repair" w installatorze. Kiedy myślałam, że zrobiłam już wszystko okazało się, że trzeba jeszcze zmienić ustawienia w BIOSie :)))) pozdro 600
    
    KROKI KONFIGURACJI:
    1) **localhost login:** root
    2) *żeby skonfigurować system (generalnie jest opisane co można sobie porobić):* setup-alpine
    3) **select keyboard layout:** pl
    4) **select variant** *(nie wiem o co chodzi z wariantami ale jak się wpisze tylko pl to będzie ten basic)*: pl
    5) **Enter system hostname** *(czyli nazwę użytkownika ALE chyba nie do końca bo była mowa że można tu podać nazwę domeny serwera(?) np. krakow.uek.pl, co ciekawe, nazwa może posiadać TYLKO małe litery):* olga
    6)*kolejny krok informuje o dostępnych interfejsach:* eth0 *(lub po prostu klikając enter)*
    7) *tutaj ustalamy w jaki sposób zaadresować ip*: dhcp *(został przydzielony mi zadres ip 10.0.2.15)*
    8) **Do you want to do any manual network configuration?"** no
    9) **New password:** ssowusiak
    10) **Which timezone are you in?:** Poland
    11) *tutaj zapytanie o serwer proxy*: none
    12) **Which NTP client to run? ('busybox', 'openntpd', 'chrony', or 'none')** *(nie wiem za bardzo co to klient NTP - klient który będzie dbał o to aby czas w naszym systemie był poprawnie ustawiony):* chrony
    13)**Enter mirror number (1-46) or URL to add** *(repozytoria(?))*: f *wybierze najszybsze repozytorium*
    14) **Which SSH server?:** openssh
    15) **Which disk would you like to use?** *(jesli wybierzemy none to wszystko będzie trzeba od nowa robić więc tego nie chcemy!)*: sda
    16) **How would you like to use it?** *(w ? jest sporo info o tym np. lvm tworzy 'kolejną warstwę abstrakcji' która pozwala jakoś zarządzać jeszcze tymi dyskami)*: lvmsys
    17) **Erase the above disk?:** yes
    18) *po instalacji powinno się wyciągnąć z pamięci alpine i uruchomić ponownie* -- tylko czemu usuwać z pamięci(?)
    
    
   * [Linux Debian](https://www.debian.org/)
   * [Linux CentOS](https://www.centos.org/)
   * Windows 

2. Sprawdź oraz przygotuj charakterystykę dla przykładowego urządzenia w Twojej sieci domowej
   * Adres
   * Maska
   * Adres bramy
   * DNS 1
   * DNS 2
  
    Przygotuj dokumentację graficzną Twojej sieci domowej, uwzględnij adresy i urządzenia

3. Zarejestruj konto w CISCO Academy celem pobrania Packet tracer
   https://www.netacad.com/courses/packet-tracer

4. Dlaczego umiejętnosci z zakresu sieci komputerowych mogą mi się przydać? :)


### Charakterystyka systemu operacyjnego

| Charakterystyka           | wartość               | komentarzu                |
| -------------             |:-------------:        | -----:                    |
| nazwa                     | linux                 | centos 7                  |
| cfg interfejsów           | centos 7 | /etc/sysconfig/network-scripts         |
| program (parametry sieci) | niewiem               |                           |
| ....                      | .....                 |                           |
| nazwa                     | Alpine Linux          |                           |
| Konfiguracja ip           | ``$ ip all ``         | show all eth interfaces   |
| Tablica routingu          | ``$ ip route show ``  | what is gateway?!         |
| check nameservers (DNS)   | ``$ cat /etc/resolv.conf ``  | which DNS were set |
| funfact                   | ctr + l               | czyści ekran              |
| ....                      | .....                 |                           |
| nazwa                     | Windows       |                           |
| wszystkie info o ip, dns, bramach itd.    | ipconfig   |    |
| więcej info m.in DNS    | ipconfig -all |         |
|    |   |  |
| 

### Konfiguracja połączenia sieciowego

| Parametr | wartość           | komentarzu |
| ------------- |:------:| -----:|
| Adres IP      | 10.0.2.15 | przydzielony przez DHCP |
| Maska podsieci| 10.0.2.15/24 | 255.255.255.0        |
| Brama         | 10.0.2.2     | default from route table |
| DNS 1         | 192.168.2.1 | cat /etc/resolv.conf |
| DNS 2         |  |  |
                | nslookup *adres strony*| Podaje ip serwera danej stronki |
| ------------- |:----:| -----:|
| Windows | LAN Wi-Fi |  |
| Adres IP      | 192.168.2.35 | przydzielony przez DHCP |
| Maska podsieci| 192.168.2.35/24 | 255.255.255.0        |
| Brama         | 192.168.2.1    | default from route table |
| DNS 1         | 192.168.2.1 | ipconfig -all |
| DNS 2         |  |  |
                

### Schemat sieci

aby załączyć obrazek 

```markdown
![alt schemat](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png)![alt schemat](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png)

![alt schemat](images/my-network-schema.png)
```

![my network](network.png)

