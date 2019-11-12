# Isochronie


Le point d'entrée principale est de l'api REST de calcul d'isochronie est :

https://ggo-rest-api.appspot.com/api/rest/geoservice/direction/isochrone

`GET <BASE_REST_ENTRY_POINT>?center=<latitude,longitude>&time_limits=<time_ranges>&profile=<route_profile>&substract_geometries=<true|false>`

Le paramètre "time_limits" contient une liste des temps en minutes. 

Exemple pour calculer des isochrones de 5 et 10 minutes

`time_limits=5,10`

Le paramètre optionnel "profile" définit la méthode utilisée pour calculer les isochrones (si ce paramètre n'est pas précisé dans la requête, "driving-car" est utilisé par défaut)

`profile=driving-car | foot-walking`

Le paramètre optionnel "substract_geometries" indique s'il faut renvoyer des polygones creux (par défaut: true)

`substract_geometries= true | false`


**Réponse**
La requête renvoie un GeoJSON de type FeatureCollection contennant l'ensemble des isochrones triés par intervalle de temps décroissant

```js
{
    "geocoding": {
        // informations concernant la requête
    },
    "type": "FeatureCollection",
    "features": [   ], // tableau de features
    "bbox":  // bbox de l'ensemble des features
}

```

**Exemple**

`https://ggo-rest-api.appspot.com/api/rest/geoservice/direction/isochrone?center=48.8240267,2.3584248&time_limits=5`

**Réponse**
```json
{
  "type":"FeatureCollection",
  "features":[{
  "type":"Feature",
    "geometry":{
      "type":"Polygon",
     "coordinates":[[[2.325009,48.827755],[2.327617,48.817836],[2.332349,48.813465],[2.335591,48.810636],[2.344102,48.803843],[2.344134,48.803829],[2.345968,48.803875],[2.355262,48.806469],[2.362908,48.801856],[2.36629,48.803088],[2.376102,48.80418],[2.3764,48.804311],[2.377878,48.807277],[2.383811,48.816574],[2.38733,48.822685],[2.387977,48.824178],[2.387103,48.825918],[2.385541,48.829162],[2.38151,48.836378],[2.381113,48.840748],[2.381096,48.840819],[2.380824,48.841156],[2.380564,48.841459],[2.379028,48.842101],[2.370109,48.842538],[2.363399,48.844976],[2.352387,48.844798],[2.342452,48.842675],[2.336251,48.841398],[2.336126,48.841359],[2.336075,48.841344],[2.335056,48.84032],[2.331459,48.835841],[2.325329,48.829185],[2.325289,48.829139],[2.325009,48.827755]]]
    },
    "properties":{"value":5,"bucket":0,"label":"5 min"}
  }]
}
```




