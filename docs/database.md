# Database

## MongoDB

MongoDB is een open source document-georiënteerde database en is geschreven in C++. Er is geen schema, de documenten worden in de vorm van BSON (binair JSON) opgeslagen en de structuur van deze documenten is flexibel. De database kan gemakkelijk gedistribueerd worden, de data wordt dan over meerdere computers verspreid om gedistribueerde gegevensverwerking mogelijk te maken. MongoDB is geen relationeel databasemanagementsysteem, er is geen ondersteuning voor joins en voldoet ook niet aan de ACID-regels want de ondersteuning voor transacties is beperkt. MongoDB wordt gerekend tot de zogenaamde NoSQL-databases.

MongoDb is geschikt voor grote data het is schaalbaar en werk zonder relaties in tegenstelling tot bijvoorbeeld SQLite. Omdat we in ons project geen echte relaties nodig hebben is de keuze daarom ook makkelijk gemaakt voor MongoDB.

## Database structuur

### Collection polls

```json
{
  "_id" : "1111c298aeb541d0776a9556",
  "name": "Amerikaanse verkiezingen",
  "options": {
    "Donald Trump": 10,
    "Hilary Clinton": 9,
    "Gary Johnson": 2,
    "Jill Stein": 1
  },
  "user": {
    "_id" : "45894298bee541d0776a4445",
    "username": "maliekmeersschaert"
  }
}
{
  "_id" : "2222c298aeb541d0776a9556",
  "name": "Lievelingskleur",
  "options": {
    "Geel": 1,
    "Blauw": 2
  },
  "user": {
    "id": "useridofmaliek",
    "username": "maliekmeersschaert"
  }
}
{
  "_id" : "3333c298aeb541d0776a9556",
  "name": "Kom je naar mijn feestje?",
  "options": {
    "ja": 30,
    "nee": 5
  }
}
```

### Collection users

```json
{
  "_id" : "45894298bee541d0776a4445",
  "username": "maliekmeersschaert",
  "name": "Maliek Meersschaert",
  "password": "SOME HASH",
  "polls": {
    "1": {
      "name": "Amerikaanse verkiezingen"
    },
    "2": {
      "name": "Lievelingskleur"
    }
  }
}
```
 
## Veldnamen

* users: veld met informatie van user
    * user_id: unieke id per user (eventueel later automatisch gegenereerd voor anonieme polls)
        * username: naam van de user ==> string
        * password: paswoord van de user ==> hash
        * collection polls: alle polls die bij de user horen
            * id: unieke id van de poll    
                * name: naam van de poll ==> string    
                * collection options: de mogelijkheden van de poll
                    * "Option": <value>: de keuze en bijhorende value
