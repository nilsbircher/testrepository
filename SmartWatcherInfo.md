# SmartWatcher Additional Information 

## What is SmartWatcher?

SmartWatcher ist ein Showcase Projekt der attempto welches dazu dienen soll, die Smartphone-Nutzung durch ein Spiel mit Wetteinsatz (Ether) zu kontrollieren. Zugriff auf die Applikation ist entweder durch eine klassische App oder durch eine moderne Website möglich. 
Die Spieler wetten dabei, dass sie ihr Smartphone während einem bestimmten Zeitraum nicht mehr als eine bestimmte Anzahl pro Tag beutzen. Hierbei zählt momentan die Anzahl der Aktivierungen / Entsperrungen des Smartphones. Sobald die bestimmte Zahl überschritten wird, verliert der Spieler einen Teil seines Einsatzes. Somit haben Spieler nicht nur die Möglichkeit, das eingesetzte Geld zurück zu gewinnen, sondern basierend auf dem Verhalten der anderen Spieler, mehr Geld zu gewinnen als Anfangs eingesetzt wurde. 
Die Verluste / Gewinne werden bereits am Ende des Tages realisiert und werden nach Abzug einer bestimmten Gebühr den Spielern gutgeschrieben. 
Die komplette Logik der Gewinn- und Verlustberechnungen liegt in SmartContracts in der Ethereum Blockchain (momentan privates Testnetz). Ein Server sammelt die Aktivierungszahlen und übergibt sie am Ende des Tages an diese Contracts. Er dient auch dazu Daten aus den Contracts auszulesen und diese an die Apps zur Anzeige zu übergeben.

## How to get it to run on Windows?

Um die Umgebungen auf Windows zum laufen zu bringen werden verschiedene Komponenten benötigt. Diese werden unten aufgelistet und es wird beschrieben, was es bei der Installation/beim Betrieb zu beachten gibt. 

##### Geth

Geth runs a full Ethereum node implemented in Go and is needed for the project. In order for everything to work properly one needs Version 1.5.9 and it can be dowloaded [here:](https://geth.ethereum.org/downloads/ "Ethereum Geth Node"). 
Geth is a command line tool and hence it is started in the command line from where we will use it later on to create our private Blockchain 
Der Server muss sich dann mit dieser Ethereum-Node verbinden und dies muss später in der Configurationsdatei des Severs festgehalten werden, mehr dazu im Abschnitt "Server". 



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

