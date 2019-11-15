# IRIS 2019 et données INSEE

Le point d'entrée principale est de l'api REST de la base IRIS (nommé 'BASE_SERVICE_ENTRY_POINT') est :

`<BASE_API_ENTRY_POINT>/insee/iris`

## Description des données

`GET <BASE_SERVICE_ENTRY_POINT>`

Renvoie la description des colonnes avec leur nom, type et description.

**Exemple**

`https://ggo-rest-api.appspot.com/api/insee/iris`

**Réponse**
```js
{
  "columns": [{
      "name": "INSEE_COM",
      "type": "STRING",
      "description": "Code du département suivi du numéro de commune ou du numéro d'arrondissement municipal suivi du numéro d'IRIS"
    },
    {
      "name": "NOM_COM",
      "type": "STRING",
      "description": "Code de la région"
    },
    {
      "name": "IRIS",
      "type": "STRING",
      "description": "Code du département"
    },
    {
      "name": "CODE_IRIS",
      "type": "STRING",
      "description": null
    },
    {
      "name": "NOM_IRIS",
      "type": "STRING",
      "description": null
    },
    ...
    {
      "name": "P16_POP1564",
      "type": "FLOAT64",
      "description": "Nombre de personnes de 15 à 64 ans"
    },
    {
      "name": "P16_POP1524",
      "type": "FLOAT64",
      "description": "Nombre de personnes de 15 à 24 ans"
    },
    ...
  ]
}
```

## Statistiques

`POST <BASE_SERVICE_ENTRY_POINT>/stats`

**Réponse**
La requête renvoie des indicateurs calculés sur l'ensemble des IRIS dont le centroid se trouve à l'intérieur de la géométrie de l'isochronie passé en paramètre.

Corps de la requête:

```js
{
 "summary_fields" : "[tableau des champs à aggréger avec la fonction d'aggrégation à utiliser]",
 "isochonie": {... } // la géométrie de l'isochronie
}
```

**Exemple**

`https://ggo-rest-api.appspot.com/api/insee/iris/stats`

Corps:
```json
{
  "summary_fields" : [
    { "field":"P16_POP1564", "aggregate_function": "SUM" },
    { "field":"P16_POP1524", "aggregate_function": "SUM" }
  ],
 "isochronie": {"coordinates":[[[2.336262,48.827083],[2.339893,48.819938],[2.343796,48.816721],[2.35376,48.812841],[2.361552,48.811577],[2.361896,48.811685],[2.368695,48.814638],[2.36898,48.814858],[2.375565,48.823393],[2.374865,48.829338],[2.374691,48.829654],[2.370948,48.836137],[2.360838,48.838949],[2.351576,48.837503],[2.350892,48.837083],[2.344003,48.830957],[2.336314,48.82744],[2.336262,48.827083]]],"type":"Polygon"}
}
```

**Réponse**
```js
{
    "nb_iris": 66,
    "P16_POP1564": 118613.09206959164,
    "P16_POP1524": 24637.302056662367
}
```

note: nb_iris est toujours renvoyé.






