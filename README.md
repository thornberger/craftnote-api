# Craftnote-api

Diese API ermöglicht die automatisierte Erstellung von Projekten in der Craftnote App. JSON und XML

## Server-URL

https://europe-west1-craftnote-live.cloudfunctions.net


## Endpoints

- [`POST /v1/createproject/`]


## Modelle


## Beispielabfrage JSON

```sh
curl https://europe-west1-craftnote-live.cloudfunctions.net/v1/createproject/ \
  -X POST \
  -H 'Content-type: application/json' \
  -d '{
  "name": "API-Testprojekt",
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
'
```

## Beispielabfrage XML

## Response

```sh
{
  "webLink": "https://app.mycraftnote.de/#/project?id=0DDAAAA9-2508-4AAF-A576-E91E76EA8CDB",
  "appDeepLink": "mycrafty://project?id=0DDAAAA9-2508-4AAF-A576-E91E76EA8CDB"
}
```



