## Struktura adresu IP

```192.168.100.192```
```255.255.255.0```




### Jak policzyć?
#### Adres sieci

1. 192.168.100.192 -->11000000.10101000.01100100.11000000
   255.255.255.0 -->  11111111.11111111.11111111.00000000 (24 bity na adres sieci)
2.      AND:          11000000.10101000.01100100.00000000 --> 192.168.100.0
3.

#### Adres rozgłoszeniowy

1. Odwrotność maski sieci:      00000000.00000000.00000000.11111111
2. Adres sieci:192.168.100.0 -->11000000.10101000.01100100.00000000
3. Adres rozgłoszeniowy to SUMA:11000000.10101000.01100100.11111111  --> 192.168.100.255 


## Podział na równą ilość podsieci

```2^S >= n```

Chcemy 7 -> 2^3 >= 7

Maska -> 255.255.255.11100000 -> 255.255.255.224 -> /27


## Wprowadzenie
## 
## | dziesiętnie |  binarnie   | 
| ``10``  |  | 
| ``92``  | | 
| ``37``  | | 
| ``240`` | | 
| ``192`` | | 
| ``255`` | | 
| ``128`` | | 
| ``168`` | | 

## 
## | binarnie |  dziesiętnie   | 
| ``00100000``  |  | 
| ``11111000``  | | 
| ``10100000``  | | 
| ``00110000`` | | 
| ``10101100`` | | 
| ``01000000`` | | 
| ``11111100`` | | 
| ``01100010`` | | 
 
## Notacja CIDR
##  
## | maska |  /(X) x - liczba bitów   | 
| ``255.255.255.0``   | 24 | 
| ``255.128.0.0``     | 9 | 
| ``255.255.252.0``   | 22 | 
| ``255.255.254.0``   | 23 | 
| ``255.255.255.240`` | 28 | 
| ``255.240.0.0``     | 12 | 
## 
## | CIDR |  Maska   | 
| ``/8``    | 255.0.0.0| 
| ``/20``   | 255.255.240.0 | 
| ``/30``   | 255.255.255.252 | 
| ``/16``   | 255.255.0.0 | 
| ``/27``   | 255.255.255.224 | 
| ``/11``   | 255.224.0.0 | 


## Liczba hostów
## 
## | sieć |  liczba   | 
| ``10.0.0.0/8``    | 2^(32-8) - 2 =  16 777 214| 
| ``172.16.0.0/16``   | 2^(32-16) - 2 = 65 534 | 
| ``192.168.1.0/24``   | 2^(32-24) - 2 = 254 |
| ``192.168.1.0/27``   | 2^(32-27) - 2 = 30 |
| ``192.168.1.0/29``   | 2^(32-29) - 2 = 8 |
| ``192.168.1.0/31``   | 2^(32-31) - 2 = 0 |

* liczba 0 w masce? -- to też jest sposób na policzenie liczby hostów (trzeba pamiętać o odjęciu adresiu sieci i adresu rozgłoszeniowego


## Parametry na podstawie adresu

Mając dany adres hosta i maskę znajdź:
  * adres sieci
  * początkowy adres hosta w sieci
  * liczbę hostów w zadanej podsieci ```2^(32 bity - bity maski maska) - 2 (siec i broadcast)```
  * końcowy zakres adresu hosta w sieci
  * adres rozgłoszeniowy
##   ## 

## | Parametr |  wartość   | 
| ``ip``    | 192.168.1.145| 
| ``maska``   | 255.255.255.128 | 
| ``adres sieci``   | 192.168.1.128 |
| ``liczba hostów``   | 126|
| ``host - min``   |192.168.1.129 | 
| ``host - max``   | 192.168.1.254| 
| ``broadcast``   | 192.168.1.255 | 
 
## Zadanie

0. Znajdz wszystkie parametry sieci dla hosta o adresie 172.16.128.64 / 16
##   
## | Parametr |  wartość   | 
| ``ip``    | 172.16.128.64 | 
| ``maska``   | 255.255.0.0 | 
| ``adres sieci``   | 172.16.0.0 |
| ``liczba hostów``   | 2(32-16) - 2 = 65 534 |
| ``host - min``   | 172.16.0.1 | 
| ``host - max``   | 172.16.255.254 | 
| ``broadcast``   | 172.16.255.255 | 

1.
  * Podziel sieć ```192.168.1.0``` na 16 równych podsieci
##   
## | Adres sieci |  zakres hostów   | Adres Rozgłoszeniowy |
| ``192.168.1.0``    | 1-14 | ``192.161.1.15`` |
| ``192.168.1.16``| 17-30 | ``192.161.1.31``|
| ``192.168.1.32`` |  33-46 | ``192.161.1.47``|
| ``192.168.1.48`` |  49-62 | ``192.161.1.63``|
| ``192.168.1.64``| 65-78 |``192.161.1.79`` |
| ``192.168.1.80``   | 81-94  | ``192.161.1.95``|
| ``192.168.1.96``   | 97-110  |``192.161.1.111`` |
| ``192.168.1.112``   |  113-126 | ``192.161.1.127``|
| ``192.168.1.128``   | 129 - 142  | ``192.161.1.143``|
| ``192.168.1.144``   | 145-158  |``192.161.1.159`` |
| ``192.168.1.160``   | 161-174  |``192.161.1.175`` |
| ``192.168.1.176``   | 177-189  |``192.161.1.190`` |
| ``192.168.1.192``   | 193-206  |``192.161.1.207`` |
| ``192.168.1.208``   |  209-222 | ``192.161.1.223``|
| ``192.168.1.224``   | 225-238  |``192.161.1.239`` |
| ``192.168.1.240``   | 241-254  | ``192.161.1.255``|

2. 
  * Podziel sieć ``172.16.0.0/16`` na 6 równych podsieci.

3. 
  * Podziel sieć ``192.168.1.0/24``, tak aby każda podsieć miała 11 użytkowników.

Tak jak w zadaniu 1. (?)

4. 
  * Podziel sieć ``10.0.0.0/8`` na 5 podsieci. 
    * Podsieć A ma posiadać 100 000 użytkowników, ``10.0.0.0/15`` - ``10.1.255.255/15``
    * B – 10 000 użytkowników ``10.2.0.0/18`` - ``10.2.63.255/18``
    * C – 3 000 użytkowników  ``10.2.64.0/20`` - ``10.2.79.255/20``
    * D – 500 użytkowników ``10.2.80.0/23`` - ``10.2.81.255/23``
    * E – 2 użytkowników. ``10.2.82.0/30`` - ``10.2.82.4/30``
    
## Wizualizacja

![krakow siec akademicka](cracow-core.jpeg)


## Materiały

    * http://www.cyfronet.krakow.pl/sieci/13152,artykul,charakterystyka_sieci.html
    * https://www.computerworld.pl/news/Sieci-szkieletowe-polskich-operatorow,394360.html
    * https://cidr.xyz/
