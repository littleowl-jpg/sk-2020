# NAT - Network address translation

## Symulacja

![zadanie 7](network.svg)

W którym miejscu następuje zmaina adresu prywatnego na publiczny?

Podczas przejścia przez domowy router. Zamiana występuje w warstwie sieciowej. 

Zalety NAT:
- nie trzeba używać adresów publicznych wewnątrz sieci lokalnej,
- kontrola nad portami

## Zadanie

![zadanie 7](nat-1.svg)

1.
   * Przygotuj konfigurację sieci zgodnie z powyższym diagramem
   * Zweryfikuj poprawność połączenia z siecią internet dla ``PC0``
      * adresacja
      * konfiguracja DHCP (opcjonalna ale wygodna) 
   * W pierwszej kolejności przygotuj ``PC0``, ``PC-1``
   * Upewnij się o poprawnej konfiguracji parametru systemu ``ip_forward`` dla ``PC0``
   
   ``iptables`` 
   ``sysctl net.ipv4.ip_forward=1``
   ``iptables -t nat -L``  - pokazuje tablice
   
   * Do konfiguracji wykorzystaj właściwą konfigurację ``VirtualBox`` która pozwoli na dostęp do internetu dla ``PC-1`` za pomocą interfejsu ``eth0``
   * Wykonaj konfigurację translacji adresów tak aby udostępnic komunikację z siecią internet dla ``PC-2``
   
   ``iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE``
   
   * Przygotuj dokumentację powyższego procesu
   *  **czy istnieje różnica jeżeli adres eth0 statyczny/dynamiczny? Jeżeli to jaka?**


![zadanie 7](nat-2.svg)

1. 
    * Przygotuj konfigurację sieci zgodnie z powyższym diagramem
    * Wykonaj konfigurację translacji adresów tak aby udostępnic komunikację z siecią internet dla ``PC-2`` oraz ``PC-3``
    
2. 
    * Jeżeli konfiguracja była do tej pory statyczna, rozszerz architekturę o automatyczną konfigurację hostów w podsieciach ``192.168.64.192/27`` oraz ``172.16.95.216/29`` z wykorzystaniem usługi ``DHCP``


## Zadanie do domu

1. Zapoznaj się z pojęciem Maskarady IP ``MASQUERADE``

Maskarada polega na "zamaskowaniu" większej ilości hostów z prywatnym IP za jednym urządzeniem podłączonym do internetu. To znaczy, że wszystkie urządzenia wewnętrzne w sieci można podłaczyć do internetu tylko za pomocą jednego urządzenia z publicznym IP. maskarada oprócz adresu IP podmienia również porty.
  
## Materiały

* https://tools.ietf.org/html/rfc1918
* https://linux.die.net/man/8/iptables
