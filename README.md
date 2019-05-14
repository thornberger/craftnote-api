# Craftnote-api

Diese API ermöglicht die automatisierte Erstellung von Projekten in der Craftnote App. 
Aktzeptierte Formate
1. JSON 
2. XML

## Server-URL

https://api.craftnote.de


## Endpoints

- [`POST /v1/createproject/`]

## Verifzierung

Die Verifizierung des Accounts erfolgt über einen APIKEY den man durch die mycraftnote digital Gmbh erhält.
Für Informationen und die Beantragung eines API-Keys schreibt an api@mycraftnote.de

## Swagger

Die beiliegende instructions.json kann unter
https://editor.swagger.io/
eingelesen werden

## Modelle

response
```sh
webLink*	string
example: https://app.mycraftnote.de/#/project?id=0DDAAAA9-2508-4AAF-A576-E91E76EA8CDB
The link to the created project which can be opened in a browser

appDeepLink*	string
example: mycrafty://project?id=0DDAAAA9-2508-4AAF-A576-E91E76EA8CDB
The deeplink to the created project which can be opened in a mobile client
```

Project
```sh
name*	string
example: Wasserrohrbruch
The name of the project

orderNumber	string
example: 12312344d
The ordernumber of the project

street	string
pattern: [a-zA-ZßäöüÄÖÜ .\\/-]+ [0-9a-z \\/-]*$
example: Bahnhofstr. 12
The street of the project

zipcode	string
pattern: ^[0-9a-zA-ZäÄöÖüÜß ]{4,}$
example: 70174
The zipcode of the project

city	string
pattern: [a-zA-ZäöüÄÖÜ .\\/-]+
example: Stuttgart
The city of the project

contacts	[...]
billingCity	string
pattern: [a-zA-ZäöüÄÖÜ .\\/-]+
example: Stuttgart
The billing city of the projeect
```

Contacts
```sh
name*	string
pattern: ^[a-zA-ZäÄöÖüÜß ]+([ -][a-zA-Z ]+)*$
example: Herr Maier
The name of the contact

email	string
pattern: [A-Z0-9a-z._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,}
example: maier@test.de
The email of the contact

phone	string
pattern: ^\+*[0-9]+
example: +49 711 21893732232
The phone of the contact
```

## Beispielabfrage JSON

```sh
curl https://europe-west1-craftnote-live.cloudfunctions.net/v1/createproject/ \
  -X POST \
  -H 'Content-type: application/json' \
  -d '{
  "name": "Testprojekt",
  "orderNumber": "12312344",
  "street": "Bahnhofstr. 12",
  "zipcode": "70134",
  "city": "Stuttgart",
  "contacts": [
    {
      "name": "Herr Huber",
      "email": "huber@mycraftnote.de",
      "phone": "+49 711 21893732232"
    }
  ],
  "billingCity": "Stuttgart"
}
```

## Beispieldatei XML

```sh
<?xml version="1.0" encoding="UTF-8"?>
<Project>
	<name>Testprojekt</name>
	<orderNumber>12312344d</orderNumber>
	<street>Bahnhofstr. 12</street>
	<zipcode>70589</zipcode>
	<city>Stuttgart</city>
	<contacts>
		<name>Herr Maier</name>
		<email>huber@mycraftnote.de</email>
		<phone>+49 711 21893732232</phone>
	</contacts>
	<billingCity>Stuttgart</billingCity>
</Project>

```
## Response

```sh
{
  "webLink": "https://app.mycraftnote.de/#/project?id=0DDAAAA9-2508-4AAF-A576-E91E76EA8CDB",
  "appDeepLink": "mycrafty://project?id=0DDAAAA9-2508-4AAF-A576-E91E76EA8CDB"
}
```



