# Database

## MongoDB

MongoDB is een opensource document-georiënteerde database en is geschreven in C++. Er is geen schema, de documenten worden in de vorm van BSON (binair JSON) opgeslagen en de structuur van deze documenten is flexibel. De database kan gemakkelijk gedistribueerd worden, de data wordt dan over meerdere computers verspreid om gedistribueerde gegevensverwerking mogelijk te maken. MongoDB is geen relationeel databasemanagementsysteem, er is geen ondersteuning voor joins en voldoet ook niet aan de ACID-regels want de ondersteuning voor transacties is beperkt. MongoDB wordt gerekend tot de zogenaamde NoSQL-databases.

MongoDb is geschikt voor grote data het is schaalbaar en werk zonder relaties in tegenstelling tot bijvoorbeeld SQLite. Omdat we in ons project geen echte relaties nodig hebben is de keuze daarom ook makkelijk gemaakt voor MongoDB.

### Voorbeeld eventuele database structuur

```java
{
   user_id: "1",
   username: "Maliek Meersschaert",
   password: "SOME HASH",
   polls: [
                {
                  poll_id: "1",
                  name: "Amerikaanse verkiezingen",
                  options: ["Donald Trump", "Hilary Clinton", "Gary Johnson", "Jill Stein"],
                  values: [10,9,2,1]
                },
                {
                  poll_id: "2",
                  name: "Lievelingskleur",
                  options: ["Geel", "Blauw"],
                  values: [1,2]
                }
              ]
 }
 ```
 ### Veldnamen

* user_id: unieke id per user
* username: naam van de user ==> string
* password: paswoord van de user ==> hash
* collection polls: alle polls die bij de user horen

    * poll_id: unieke id van de poll
    
    * name: naam van de poll ==> string
    
    * options: de mogelijkheden van de poll ==> array van strings

    * values: de waarden die bij elke keuze hoort ==> array van integers