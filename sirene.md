# Recherche dans la base SIRENE

Le point d'entrée principale est de l'api REST de recherche dans la base SIRENE est :

https://ggo-rest-api.appspot.com/api/rest/sirene

## Univers

`GET <BASE_REST_ENTRY_POINT>/univers`

Renvoie la liste des univers en tant que liste de chaîne de caractères.

**Exemple**

`https://ggo-rest-api.appspot.com/api/rest/sirene/univers`

**Réponse**
```json
[
    "Beatué / Santé",
    "Bricolage",
    "Chaussure",
    "Culture / Loisirs",
    "Décoration",
    "Electrodomestique",
    "Jardinerie / LISA",
    "Jouet",
    "Maroquinerie",
    "Meuble",
    "Mode",
    "Optique",
    "Sport",
    "Téléphonie"
]
```

## Mon réseau

`GET <BASE_REST_ENTRY_POINT>/mynetwork?enseigne=<enseigne>&univers=<univers>`

**Réponse**
La requête renvoie un GeoJSON de type FeatureCollection dont la propriété "features" contient la liste des établissements pour une enseigne et un univers donnés.

**Exemple**

`https://ggo-rest-api.appspot.com/api/rest/sirene/mynetwork?enseigne=Maisons du monde&univers=Meuble`

**Réponse**
```js
{
  "type": "FeatureCollection",
  "features": [{
    "type": "Feature",
    "properties": {
      "enseigne": "MAISONS DU MONDE",
      "siret": "38319665601019",
      "adresse": "RUE DES DOCTEURS CHARCOT",
      "codepostal": "42100",
      "commune": "SAINT ETIENNE",
      "departement": "LOIRE",
      "region": "AUVERGNE-RHONE-ALPES"
    },
    "geometry": {
      "type": "Point",
      "coordinates": [4.392379, 45.420415 ]
    }
  },
  {
    "type": "Feature",
    "properties": {
      "enseigne": "MAISONS DU MONDE",
      "siret": "38319665602116",
      "adresse": "CAR DES QUATRE CHEMINS",
      "codepostal": "83130",
      "commune": "LA GARDE",
      "departement": "VAR",
      "region": "PROVENCE-ALPES-COTE D'AZUR"
    },
    "geometry": {
      "type": "Point",
      "coordinates": [6.026269, 43.137528]
    }
  },
  ...   
}
```

## Ma Concurrence

`POST <BASE_REST_ENTRY_POINT>/mycompetitors`

**Réponse**
La requête renvoie un GeoJSON de type FeatureCollection dont la propriété "features" contient la liste des établissements concurrence pour une enseigne, un univers donnés et une zone

Corps de la requête

```json
{
 "enseigne" : "<enseigne>",
 "univers": "<univers>",
 "isochonie": {... } // la géométrie de l'isochronie
}
```

**Exemple**

`https://ggo-rest-api.appspot.com/api/rest/sirene/mycompetitors`

Corps:
```json
{
 "enseigne" : "MaisoNs du monde",
 "univers": "Meuble",
 "isochonie": {"coordinates":[[[2.336262,48.827083],[2.339893,48.819938],[2.343796,48.816721],[2.35376,48.812841],[2.361552,48.811577],[2.361896,48.811685],[2.368695,48.814638],[2.36898,48.814858],[2.375565,48.823393],[2.374865,48.829338],[2.374691,48.829654],[2.370948,48.836137],[2.360838,48.838949],[2.351576,48.837503],[2.350892,48.837083],[2.344003,48.830957],[2.336314,48.82744],[2.336262,48.827083]]],"type":"Polygon"}
}
```

**Réponse**
```js
{
  "type": "FeatureCollection",
  "features": [{
    "type": "Feature",
    "properties": {
      "enseigne": "HOMESELEKT SAS",
      "siret": "75035657800039",
      "adresse": "10 RUE PIERRE BROSSOLETTE",
      "codepostal": "94270",
      "commune": "LE KREMLIN BICETRE",
      "departement": "VAL-DE-MARNE",
      "region": "ILE-DE-FRANCE"
    },
    "geometry": {
      "type": "Point",
      "coordinates": [2.359234, 48.815142]
    }
  },
  {
    "type": "Feature",
    "properties": {
      "enseigne": "FAIRY",
      "siret": "34070155600011",
      "adresse": "28 AV DES GOBELINS",
      "codepostal": "75013",
      "commune": "PARIS 13",
      "departement": "PARIS",
      "region": "ILE-DE-FRANCE"
    },
    "geometry": {
      "type": "Point",
      "coordinates": [2.351973, 48.836176]
    }
  },
  ...   
}
```






