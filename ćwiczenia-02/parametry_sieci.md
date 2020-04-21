## Ustawianie parametrów sieci

### Zadania

0. Z wykorzystaniem dowolnych systemów operacyjnych na których potrafisz uruchomić interpreter ``python`` oraz oprogramowania virtualbox odwzoruj poniższy schemat sieci:

W Alpine: 

```*apk add git*```

```*apk add python3*```

![alt text][network]

[network]: ./network.png "Logo Title Text 2"

1. na 1 z komputerów zainstaluj i uruchom program ``server.py`` dostępne pod adresem ``https://github.com/jkanclerz/client-server-chat``

    Polecenie  ```git clone https://github.com/jkanclerz/client-server-chat```

    Polecenie żeby uruchomić ```python3 serwer.py```

2. na 2 z komputerów zainstaluj i uruchom program ``client.py`` dostępne pod adresem ``https://github.com/jkanclerz/client-server-chat``

    Polecenie żeby zainstalować ```git clone https://github.com/jkanclerz/client-server-chat```
    
    Polecenie żeby uruchomić ```python3 client.py```

3. Manipulując konfiguracją sieci na poziomie virtualbox, uruchom serwer czatu, oraz udostępnij go na wybranym porcie oraz adresie tak aby istniała możliwość połączenia przez inne osoby w obrębie pracowni

    Ustawiamy nową sieć NAT w ogólnych ustawieniach VirtualBoxa a potem podłączamy maszyny do tej sieci
    

4. Zainstaluj oprogramowanie serwera HTTP ``nginx`` lub innego, skonfiguruj plik index.html wg instrukcji, sprawdź dostępność strony z wykorzystaniem dowolnego klienta protokołu ``HTTP`` z różnych konfiguracji IP

    Za pomocą polecenia ```netstat``` obserwujemy ruch w sieci
    
    ```apk add nginx```
    
    ```rc-services nginx start```
    
    
    Po ponownym wyświetleniu netstat zobaczymy nginx działajacego na porcie 80

    Tworzymy stronke:

    ```echo "Hello world" > /var/www/index.html``` - czemu taka ścieżka(?)
    
    ```apk add curl``` co to curl? - wyświetla htmla?
    
    Żeby otworzyć naszą stronkę: ``` curl 127.0.0.1```
    

    ```cat /etc/nginx/conf.d/default.conf```
    
    

5. Posługując się programami tj: ``netstat`` lub ``lsof`` sprawdź na jakich portach zostały uruchomione serwery czatu czy HTTP

Wejściowe parametry sieci
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  | 10.0.15.4 | ip addr add 10.0.15.4/24 dev eth0 *(czyli do którego interfejsu chcemy ten adres przypisać)*|
| MASKA  | /24 (255.255.255.0) | |
|   |  | |
| PC 2  |  | |
| IP - address  | 10.0.15.6 | ip addr add 10.0.15.6/24 dev eth0|
| MASKA  | /24 (255.255.255.0 )| |

Weryfikacja połączenia

Polecenie
```ping *adres ip np.* 10.0.15.6```


Efekt
```przesłane zostały pakiety potwierdzające połączenie```


Statyczna konfiguracja parametrów połączenia
Wejściowe parametry sieci
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  | 192.168.10.10 | ip addr 192.168.10.10/24 add dev eth0|
| MASKA  | 255.255.255.0 | |
|   |  | |
| PC 2  |  | |
| IP - address  | 192.168.10.11 | |
| MASKA  | 255.255.128.0 | |
| PC 2  |  | |
| IP - address  | 172.16.100.100 | |
| MASKA  | 255.255.0.0 | |

Weryfikacja połączenia

Polecenie
```
```

Efekt
```
```

Nowa statyczna konfiguracja 

-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  |  | |
| MASKA  |  | |
|   |  | |
| PC 2  |  | |
| IP - address  |  | |
| MASKA  |  | |

Weryfikacja połączenia

Polecenie
```
```

Efekt
```
```

### Utrwalenie konfiguracji

Dlaczego? Jak? Co? :)

Kiedy chcemy mieć dwa interfejsy (jeden static drugi dhcp) musimy pamiętać, żeby w ustawieniach maszyny dodać karte sieciową NAT


```auto eth0
iface eth0 inet dhcp
    hostname localhost 
    
auto eth1
iface eth1 inet static
    address *jakis adres*
    netmask 255.255.255.0

```   
Zapisujemy i wykonujemy polecenie (w alpine)
```rc-service networking restart```



### Warto wiedzieć ###

-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
| Lokalizacja pliku z konfiguracją sieci| ``` /etc/network/interfaces ``` | |
| UP -> Wyłączenie interfejsu sieciowego| ip link set eth1 up | |
| DOWN -> Włączenie interfejsu sieciowego| ip link set eth1 down| |
| Sprawdzenie obecnych parametrów | | |
| lista wszystkich interfejsów | ip a| |
| Które interfejsy jakie porty słuchają | netstat| |
