# SmartWatcher Additional Information 

## What is SmartWatcher?

SmartWatcher ist ein Showcase Projekt der attempto welches dazu dienen soll, die Smartphone-Nutzung durch ein Spiel mit Wetteinsatz (Ether) zu kontrollieren. Zugriff auf die Applikation ist entweder durch eine klassische App oder durch eine moderne Website möglich. 
Die Spieler wetten dabei, dass sie ihr Smartphone während einem bestimmten Zeitraum nicht mehr als eine bestimmte Anzahl pro Tag beutzen. Hierbei zählt momentan die Anzahl der Aktivierungen / Entsperrungen des Smartphones. Sobald die bestimmte Zahl überschritten wird, verliert der Spieler einen Teil seines Einsatzes. Somit haben Spieler nicht nur die Möglichkeit, das eingesetzte Geld zurück zu gewinnen, sondern basierend auf dem Verhalten der anderen Spieler, mehr Geld zu gewinnen als Anfangs eingesetzt wurde. 
Die Verluste / Gewinne werden bereits am Ende des Tages realisiert und werden nach Abzug einer bestimmten Gebühr den Spielern gutgeschrieben. 
Die komplette Logik der Gewinn- und Verlustberechnungen liegt in SmartContracts in der Ethereum Blockchain (momentan privates Testnetz). Ein Server sammelt die Aktivierungszahlen und übergibt sie am Ende des Tages an diese Contracts. Er dient auch dazu Daten aus den Contracts auszulesen und diese an die Apps zur Anzeige zu übergeben.

## How to get it to run on Windows?

Um die Umgebungen auf Windows zum laufen zu bringen werden verschiedene Komponenten benötigt. Diese werden unten aufgelistet und es wird beschrieben, was es bei der Installation/beim Betrieb zu beachten gibt. 

### Geth

Geth runs a full Ethereum node implemented in Go and is needed for the project. In order for everything to work properly one needs Version 1.5.9 and it can be dowloaded [here](https://geth.ethereum.org/downloads/ "Ethereum Geth Node") . 
Geth is a command line tool and hence it is started in the command line from where we will use it later on to create our private Blockchain 
Der Server muss sich dann mit dieser Ethereum-Node verbinden und dies muss später in der Configurationsdatei des Severs festgehalten werden, mehr dazu im Abschnitt "Server". 
Um die Befehle auf die eigenen Bedürfnisse anzupassen, emphiehlt es sich den Editor zu verwenden. 
Die lokale Blockchain muss nach erfolgreichem installieren von geth erst initialisiert werden und dies wird mit folgendem Befehl ausgeführt: 

```sh
geth --datadir="C:\Users\Nils Bircher\Projects\_aim_02_5_9" init "C:\Users\Nils Bircher\Projects\aim-smartwatcher\node\src\main\resources\genesis\customgenesis.json"
```
geth --datadir="C:\Users\Nils Bircher\Projects\_aim_02_5_9" init "C:\Users\Nils Bircher\Projects\aim-smartwatcher\node\src\main\resources\genesis\customgenesis.json"

Hierbei ist der erste Teil ein selbst erstelltes directory, bei mir mit dem namen "_aim_02_5_9", wobei es einen beliebigen Namen tragen kann und der Ordner an einem beliebigen Ort untergrbracht sein kann. 

Um die später benötigten Log Files sauber abzulegen emphiehlt es sich, in dem Ordner ein Unterordner mit dem namen "logs" anzulegen. 

Der zweite Teil ab init ruft dann das customgenesis File auf, welches die Parameter für die private Blockchain setzt. Nach ausführen des Befehls sollten verschieden Files im Ordner, welcher erstellt wurde, auftauchen. 

Falls etwas im genesis-File geändert werden muss oder etwas nicht funktioniert, empfiehlt es sich, alle Files im verwendeten Ordner zu löschen und den Vorgang zu wiederholen. Jedes Mal ändert sich die Adresse der enode und somit muss der Server an der Stelle, wo die enode eingesetzt wird, geändert werden und ebenfalls neu gestartet werden.


### Server

Der Server, welcher in Java geschrieben wurde, habe ich mit Eclipse geöffnet. 

Die zuvor genannte enode muss im Server eingertagen werden unter "..\aim-smartwatcher\node\target\classes\ethereumj.conf".

### Komplettes aufsetzen der lokalen Umgebung (z.B. bei einem Fehler)

1) Files aus dem angelegten Ordner löschen, folgenden befehl ausführen in der command line: "geth --datadir="C:\Users\Nils Bircher\Projects\_aim_02_5_9" init "C:\Users\Nils Bircher\Projects\aim-smartwatcher\node\src\main\resources\genesis\customgenesis.json"

2) Lokale Blockchain starten mit dem Befehl: geth --datadir="C:\Users\Nils Bircher\Projects\_aim_02_5_9" -verbosity 6 --port 30302 --networkid "8099" --ipcdisable --rpc --rpcapi "eth,personal,debug,web3" --rpcport 8101 --rpccorsdomain "*" --nodiscover --identity "master" console 2>> "C:\Users\Nils Bircher\Projects\_aim_02_5_9\logs\01.log"

--> Hierbei wird die Blockchain gestartet und die Konsole wird aufgerufen. 
--> Um den miner zu starten muss man den Befehl miner.start(1) eingeben, wobei 1 für die Anzahl der Threads benötigt wird. Bei meinem Windows Rechner lief der miner lediglich, wenn ich einen Thread angegreben habe. Evtl. mit 8 oder 4 versuchen und sonst ebenfalls 1 eingeben. 
--> Der miner wird mit dem Befehl miner.stop() gestoppt. (Die klammern werden benötigt, sonst gibt es einen Error)

3) Mit dem Befehl "admin" werden viele Informationen angezeigt, unter anderem die enode, welche für den Server benötigt wird. 

4) Enode auf dem Server eintragen und dann den Server starten. 

--> Um den Server überhaupt erfolgreich starten zu können, wird eine MongoDB benötigt. Diese kann hier heruntergeladen werden: https://www.mongodb.com/download-center?jmp=tutorials#community

--> Die MongoDB muss lediglich im Hintergrund laufen und der Server speichert dann die angelegten User etc. in der MongoDB selbständig ab. 

5) Bei gestartetem Miner sollte dann im Server ersichtlich sein, wie die Blocks vorzu geminet werden 

6) Nun kann man z.B. mit Postman getestet werden, ob man einen neuen User anlegen kann. Unter "Additional Information" wird ein separates Kapitel erstellt, wie dies genau funktioniert.




## Additional Information



# Introduction to a DApp 

X
## Table of contents

1) Blockchain - Basics
2) Ethereum - Basics 
3) XXX

## 1) Blockchain - Basics

A blockchain is a public record of transactions which is saved in a distributed manner. Hence, there are many instances of the database saved on a multitude of computers. The real change the first blockchain projects brought is how an agreement is formed to decide upon the valid version of the database and how new transactions are handled and added to the database. 

###### Inspired by the following articles: 
* https://blockgeeks.com/guides/what-is-blockchain-technology/
* https://www.ibm.com/blockchain
* https://hackernoon.com/a-beginners-guide-to-blockchain-d04266844e7
* https://www.forbes.com/sites/bernardmarr/2017/01/24/a-complete-beginners-guide-to-blockchain/#26f204c46e60
* https://medium.com/blockchain-education-network/what-is-blockchain-explained-for-beginners-5e747cea271

## 2) Ethereum - Basics

Paragraph 2

## 3) XXX

Paragraph 3

## X) Other interesting resources / Topics: 

#### Geth
* https://ethereum.stackexchange.com/questions/28703/full-list-of-geth-terminal-commands

