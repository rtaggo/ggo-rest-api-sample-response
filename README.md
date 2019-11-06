# GGO-REST-API Sample Response

Ce repository contient des exemples de réponses de l'api rest ggo sur GCP. 

# Géocodage / Reverse

Le point d'entrée principale est de l'api REST de géocodage/reverse est :

https://ggo-rest-api.appspot.com/api/rest/geoservice/geocode

## Gécodage
`GET <BASE_REST_ENTRY_POINT>/search?q=<lookup_address>`

**Réponse**
La requête renvoie un GeoJSON de type FeatureCollection dont la propriété "features" contient la liste des addresses possibles

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

`https://ggo-rest-api.appspot.com/api/rest/geoservice/geocode/search?q=87 avenue d'italie, paris`

**Réponse**
```json
{
  "geocoding":{
    "version":"0.2",
    "attribution":"http://192.168.2.20:3100/attribution",
    "query":{
      "text":"87 avenue d'italie, paris",
      "size":10,
      "private":false,
      "boundary.country":[
        "FRA"
      ],
      "lang":{
        "name":"English",
        "iso6391":"en",
        "iso6393":"eng",
        "defaulted":true
      },
      "querySize":20,
      "parser":"libpostal",
      "parsed_text":{
        "number":"87",
        "street":"avenue d'italie",
        "city":"paris"
      }
    },
    "engine":{
      "name":"Pelias",
      "author":"Mapzen",
      "version":"1.0"
    },
    "timestamp":1573030125358
  },
  "type":"FeatureCollection",
  "features":[
    {
      "type":"Feature",
      "geometry":{
        "type":"Point",
        "coordinates":[
          2.358434,
          48.824031
        ]
      },
      "properties":{
        "id":"fr/paris:540a04e70ad9a088",
        "gid":"openaddresses:address:fr/paris:540a04e70ad9a088",
        "layer":"address",
        "source":"openaddresses",
        "source_id":"fr/paris:540a04e70ad9a088",
        "name":"87 Av d'Italie",
        "housenumber":"87",
        "street":"Av d'Italie",
        "postalcode":"75013",
        "confidence":1,
        "match_type":"exact",
        "accuracy":"point",
        "country":"France",
        "country_gid":"whosonfirst:country:85633147",
        "country_a":"FRA",
        "macroregion":"Ile-of-France",
        "macroregion_gid":"whosonfirst:macroregion:404227465",
        "macroregion_a":"IF",
        "region":"Paris",
        "region_gid":"whosonfirst:region:85683497",
        "region_a":"VP",
        "localadmin":"Paris",
        "localadmin_gid":"whosonfirst:localadmin:1159322569",
        "locality":"Paris",
        "locality_gid":"whosonfirst:locality:101751119",
        "borough":"13th Arrondissement",
        "borough_gid":"whosonfirst:borough:1158894257",
        "continent":"Europe",
        "continent_gid":"whosonfirst:continent:102191581",
        "label":"87 Av d'Italie, Paris, France"
      }
    },
    {
      "type":"Feature",
      "geometry":{
        "type":"Point",
        "coordinates":[
          2.358425,
          48.824027
        ]
      },
      "properties":{
        "id":"node/2540682965",
        "gid":"openstreetmap:address:node/2540682965",
        "layer":"address",
        "source":"openstreetmap",
        "source_id":"node/2540682965",
        "name":"87 Avenue d'Italie",
        "housenumber":"87",
        "street":"Avenue d'Italie",
        "confidence":1,
        "match_type":"exact",
        "accuracy":"point",
        "country":"France",
        "country_gid":"whosonfirst:country:85633147",
        "country_a":"FRA",
        "macroregion":"Ile-of-France",
        "macroregion_gid":"whosonfirst:macroregion:404227465",
        "macroregion_a":"IF",
        "region":"Paris",
        "region_gid":"whosonfirst:region:85683497",
        "region_a":"VP",
        "localadmin":"Paris",
        "localadmin_gid":"whosonfirst:localadmin:1159322569",
        "locality":"Paris",
        "locality_gid":"whosonfirst:locality:101751119",
        "borough":"13th Arrondissement",
        "borough_gid":"whosonfirst:borough:1158894257",
        "continent":"Europe",
        "continent_gid":"whosonfirst:continent:102191581",
        "label":"87 Avenue d'Italie, Paris, France"
      }
    }
  ],
  "bbox":[
    2.358425,
    48.824027,
    2.358434,
    48.824031
  ]
}
```

## Reverse Géocodage
`GET <BASE_REST_ENTRY_POINT>/reverse?lat=<latitude>&lng=<longitude>`

**Réponse**
La requête renvoie un GeoJSON de type FeatureCollection dont la propriété "features" contient la liste des addresses possibles.

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

`https://ggo-rest-api.appspot.com/api/rest/geoservice/geocode/reverse?lat= 48.8259584&lng=2.3535616`

**Réponse**
```json
{
  "geocoding":{
    "version":"0.2",
    "attribution":"http://192.168.2.20:3100/attribution",
    "query":{
      "layers":[
        "address"
      ],
      "size":10,
      "private":false,
      "point.lat":48.8259584,
      "point.lon":2.3535616,
      "boundary.circle.lat":48.8259584,
      "boundary.circle.lon":2.3535616,
      "lang":{
        "name":"English",
        "iso6391":"en",
        "iso6393":"eng",
        "defaulted":true
      },
      "querySize":20
    },
    "engine":{
      "name":"Pelias",
      "author":"Mapzen",
      "version":"1.0"
    },
    "timestamp":1573039365129
  },
  "type":"FeatureCollection",
  "features":[
    {
      "type":"Feature",
      "geometry":{
        "type":"Point",
        "coordinates":[
          2.353455,
          48.825882
        ]
      },
      "properties":{
        "id":"fr/paris:ef14816173c6d506",
        "gid":"openaddresses:address:fr/paris:ef14816173c6d506",
        "layer":"address",
        "source":"openaddresses",
        "source_id":"fr/paris:ef14816173c6d506",
        "name":"173 Rue De Tolbiac",
        "housenumber":"173",
        "street":"Rue De Tolbiac",
        "postalcode":"75013",
        "confidence":0.8,
        "distance":0.012,
        "accuracy":"point",
        "country":"France",
        "country_gid":"whosonfirst:country:85633147",
        "country_a":"FRA",
        "macroregion":"Ile-of-France",
        "macroregion_gid":"whosonfirst:macroregion:404227465",
        "macroregion_a":"IF",
        "region":"Paris",
        "region_gid":"whosonfirst:region:85683497",
        "region_a":"VP",
        "localadmin":"Paris",
        "localadmin_gid":"whosonfirst:localadmin:1159322569",
        "locality":"Paris",
        "locality_gid":"whosonfirst:locality:101751119",
        "borough":"13th Arrondissement",
        "borough_gid":"whosonfirst:borough:1158894257",
        "continent":"Europe",
        "continent_gid":"whosonfirst:continent:102191581",
        "label":"173 Rue De Tolbiac, Paris, France"
      }
    },
    {
      "type":"Feature",
      "geometry":{
        "type":"Point",
        "coordinates":[
          2.353336,
          48.826074
        ]
      },
      "properties":{
        "id":"fr/paris:fb83d150038ec19e",
        "gid":"openaddresses:address:fr/paris:fb83d150038ec19e",
        "layer":"address",
        "source":"openaddresses",
        "source_id":"fr/paris:fb83d150038ec19e",
        "name":"160 Rue De Tolbiac",
        "housenumber":"160",
        "street":"Rue De Tolbiac",
        "postalcode":"75013",
        "confidence":0.8,
        "distance":0.021,
        "accuracy":"point",
        "country":"France",
        "country_gid":"whosonfirst:country:85633147",
        "country_a":"FRA",
        "macroregion":"Ile-of-France",
        "macroregion_gid":"whosonfirst:macroregion:404227465",
        "macroregion_a":"IF",
        "region":"Paris",
        "region_gid":"whosonfirst:region:85683497",
        "region_a":"VP",
        "localadmin":"Paris",
        "localadmin_gid":"whosonfirst:localadmin:1159322569",
        "locality":"Paris",
        "locality_gid":"whosonfirst:locality:101751119",
        "borough":"13th Arrondissement",
        "borough_gid":"whosonfirst:borough:1158894257",
        "continent":"Europe",
        "continent_gid":"whosonfirst:continent:102191581",
        "label":"160 Rue De Tolbiac, Paris, France"
      }
    },
    {
      "type":"Feature",
      "geometry":{
        "type":"Point",
        "coordinates":[
          2.353657,
          48.825772
        ]
      },
      "properties":{
        "id":"fr/paris:0f8b0361aeadbde3",
        "gid":"openaddresses:address:fr/paris:0f8b0361aeadbde3",
        "layer":"address",
        "source":"openaddresses",
        "source_id":"fr/paris:0f8b0361aeadbde3",
        "name":"66 Rue Du Moulin Des Pres",
        "housenumber":"66",
        "street":"Rue Du Moulin Des Pres",
        "postalcode":"75013",
        "confidence":0.8,
        "distance":0.022,
        "accuracy":"point",
        "country":"France",
        "country_gid":"whosonfirst:country:85633147",
        "country_a":"FRA",
        "macroregion":"Ile-of-France",
        "macroregion_gid":"whosonfirst:macroregion:404227465",
        "macroregion_a":"IF",
        "region":"Paris",
        "region_gid":"whosonfirst:region:85683497",
        "region_a":"VP",
        "localadmin":"Paris",
        "localadmin_gid":"whosonfirst:localadmin:1159322569",
        "locality":"Paris",
        "locality_gid":"whosonfirst:locality:101751119",
        "borough":"13th Arrondissement",
        "borough_gid":"whosonfirst:borough:1158894257",
        "continent":"Europe",
        "continent_gid":"whosonfirst:continent:102191581",
        "label":"66 Rue Du Moulin Des Pres, Paris, France"
      }
    },
    {
      "type":"Feature",
      "geometry":{
        "type":"Point",
        "coordinates":[
          2.353674,
          48.825765
        ]
      },
      "properties":{
        "id":"node/1938481781",
        "gid":"openstreetmap:address:node/1938481781",
        "layer":"address",
        "source":"openstreetmap",
        "source_id":"node/1938481781",
        "name":"66 Rue du Moulin des Prés",
        "housenumber":"66",
        "street":"Rue du Moulin des Prés",
        "confidence":0.8,
        "distance":0.023,
        "accuracy":"point",
        "country":"France",
        "country_gid":"whosonfirst:country:85633147",
        "country_a":"FRA",
        "macroregion":"Ile-of-France",
        "macroregion_gid":"whosonfirst:macroregion:404227465",
        "macroregion_a":"IF",
        "region":"Paris",
        "region_gid":"whosonfirst:region:85683497",
        "region_a":"VP",
        "localadmin":"Paris",
        "localadmin_gid":"whosonfirst:localadmin:1159322569",
        "locality":"Paris",
        "locality_gid":"whosonfirst:locality:101751119",
        "borough":"13th Arrondissement",
        "borough_gid":"whosonfirst:borough:1158894257",
        "continent":"Europe",
        "continent_gid":"whosonfirst:continent:102191581",
        "label":"66 Rue du Moulin des Prés, Paris, France"
      }
    },
    {
      "type":"Feature",
      "geometry":{
        "type":"Point",
        "coordinates":[
          2.353883,
          48.825905
        ]
      },
      "properties":{
        "id":"fr/paris:1c5236ad705593f3",
        "gid":"openaddresses:address:fr/paris:1c5236ad705593f3",
        "layer":"address",
        "source":"openaddresses",
        "source_id":"fr/paris:1c5236ad705593f3",
        "name":"171 Rue De Tolbiac",
        "housenumber":"171",
        "street":"Rue De Tolbiac",
        "postalcode":"75013",
        "confidence":0.8,
        "distance":0.024,
        "accuracy":"point",
        "country":"France",
        "country_gid":"whosonfirst:country:85633147",
        "country_a":"FRA",
        "macroregion":"Ile-of-France",
        "macroregion_gid":"whosonfirst:macroregion:404227465",
        "macroregion_a":"IF",
        "region":"Paris",
        "region_gid":"whosonfirst:region:85683497",
        "region_a":"VP",
        "localadmin":"Paris",
        "localadmin_gid":"whosonfirst:localadmin:1159322569",
        "locality":"Paris",
        "locality_gid":"whosonfirst:locality:101751119",
        "borough":"13th Arrondissement",
        "borough_gid":"whosonfirst:borough:1158894257",
        "continent":"Europe",
        "continent_gid":"whosonfirst:continent:102191581",
        "label":"171 Rue De Tolbiac, Paris, France"
      }
    },
    {
      "type":"Feature",
      "geometry":{
        "type":"Point",
        "coordinates":[
          2.35349,
          48.826171
        ]
      },
      "properties":{
        "id":"node/2503851125",
        "gid":"openstreetmap:address:node/2503851125",
        "layer":"address",
        "source":"openstreetmap",
        "source_id":"node/2503851125",
        "name":"64 Rue du Moulin des Prés",
        "housenumber":"64",
        "street":"Rue du Moulin des Prés",
        "confidence":0.8,
        "distance":0.024,
        "accuracy":"point",
        "country":"France",
        "country_gid":"whosonfirst:country:85633147",
        "country_a":"FRA",
        "macroregion":"Ile-of-France",
        "macroregion_gid":"whosonfirst:macroregion:404227465",
        "macroregion_a":"IF",
        "region":"Paris",
        "region_gid":"whosonfirst:region:85683497",
        "region_a":"VP",
        "localadmin":"Paris",
        "localadmin_gid":"whosonfirst:localadmin:1159322569",
        "locality":"Paris",
        "locality_gid":"whosonfirst:locality:101751119",
        "borough":"13th Arrondissement",
        "borough_gid":"whosonfirst:borough:1158894257",
        "continent":"Europe",
        "continent_gid":"whosonfirst:continent:102191581",
        "label":"64 Rue du Moulin des Prés, Paris, France"
      }
    },
    {
      "type":"Feature",
      "geometry":{
        "type":"Point",
        "coordinates":[
          2.353476,
          48.82617
        ]
      },
      "properties":{
        "id":"fr/paris:a9db2ac8753496fa",
        "gid":"openaddresses:address:fr/paris:a9db2ac8753496fa",
        "layer":"address",
        "source":"openaddresses",
        "source_id":"fr/paris:a9db2ac8753496fa",
        "name":"64 Rue Du Moulin Des Pres",
        "housenumber":"64",
        "street":"Rue Du Moulin Des Pres",
        "postalcode":"75013",
        "confidence":0.8,
        "distance":0.024,
        "accuracy":"point",
        "country":"France",
        "country_gid":"whosonfirst:country:85633147",
        "country_a":"FRA",
        "macroregion":"Ile-of-France",
        "macroregion_gid":"whosonfirst:macroregion:404227465",
        "macroregion_a":"IF",
        "region":"Paris",
        "region_gid":"whosonfirst:region:85683497",
        "region_a":"VP",
        "localadmin":"Paris",
        "localadmin_gid":"whosonfirst:localadmin:1159322569",
        "locality":"Paris",
        "locality_gid":"whosonfirst:locality:101751119",
        "borough":"13th Arrondissement",
        "borough_gid":"whosonfirst:borough:1158894257",
        "continent":"Europe",
        "continent_gid":"whosonfirst:continent:102191581",
        "label":"64 Rue Du Moulin Des Pres, Paris, France"
      }
    },
    {
      "type":"Feature",
      "geometry":{
        "type":"Point",
        "coordinates":[
          2.353822,
          48.82581
        ]
      },
      "properties":{
        "id":"node/1938481780",
        "gid":"openstreetmap:address:node/1938481780",
        "layer":"address",
        "source":"openstreetmap",
        "source_id":"node/1938481780",
        "name":"65 Rue du Moulin des Prés",
        "housenumber":"65",
        "street":"Rue du Moulin des Prés",
        "confidence":0.8,
        "distance":0.025,
        "accuracy":"point",
        "country":"France",
        "country_gid":"whosonfirst:country:85633147",
        "country_a":"FRA",
        "macroregion":"Ile-of-France",
        "macroregion_gid":"whosonfirst:macroregion:404227465",
        "macroregion_a":"IF",
        "region":"Paris",
        "region_gid":"whosonfirst:region:85683497",
        "region_a":"VP",
        "localadmin":"Paris",
        "localadmin_gid":"whosonfirst:localadmin:1159322569",
        "locality":"Paris",
        "locality_gid":"whosonfirst:locality:101751119",
        "borough":"13th Arrondissement",
        "borough_gid":"whosonfirst:borough:1158894257",
        "continent":"Europe",
        "continent_gid":"whosonfirst:continent:102191581",
        "label":"65 Rue du Moulin des Prés, Paris, France"
      }
    },
    {
      "type":"Feature",
      "geometry":{
        "type":"Point",
        "coordinates":[
          2.353845,
          48.825793
        ]
      },
      "properties":{
        "id":"fr/paris:b5602e64b187bde4",
        "gid":"openaddresses:address:fr/paris:b5602e64b187bde4",
        "layer":"address",
        "source":"openaddresses",
        "source_id":"fr/paris:b5602e64b187bde4",
        "name":"65 Rue Du Moulin Des Pres",
        "housenumber":"65",
        "street":"Rue Du Moulin Des Pres",
        "postalcode":"75013",
        "confidence":0.8,
        "distance":0.028,
        "accuracy":"point",
        "country":"France",
        "country_gid":"whosonfirst:country:85633147",
        "country_a":"FRA",
        "macroregion":"Ile-of-France",
        "macroregion_gid":"whosonfirst:macroregion:404227465",
        "macroregion_a":"IF",
        "region":"Paris",
        "region_gid":"whosonfirst:region:85683497",
        "region_a":"VP",
        "localadmin":"Paris",
        "localadmin_gid":"whosonfirst:localadmin:1159322569",
        "locality":"Paris",
        "locality_gid":"whosonfirst:locality:101751119",
        "borough":"13th Arrondissement",
        "borough_gid":"whosonfirst:borough:1158894257",
        "continent":"Europe",
        "continent_gid":"whosonfirst:continent:102191581",
        "label":"65 Rue Du Moulin Des Pres, Paris, France"
      }
    },
    {
      "type":"Feature",
      "geometry":{
        "type":"Point",
        "coordinates":[
          2.353198,
          48.825867
        ]
      },
      "properties":{
        "id":"fr/paris:0322582ce3d2e14c",
        "gid":"openaddresses:address:fr/paris:0322582ce3d2e14c",
        "layer":"address",
        "source":"openaddresses",
        "source_id":"fr/paris:0322582ce3d2e14c",
        "name":"175 Rue De Tolbiac",
        "housenumber":"175",
        "street":"Rue De Tolbiac",
        "postalcode":"75013",
        "confidence":0.8,
        "distance":0.029,
        "accuracy":"point",
        "country":"France",
        "country_gid":"whosonfirst:country:85633147",
        "country_a":"FRA",
        "macroregion":"Ile-of-France",
        "macroregion_gid":"whosonfirst:macroregion:404227465",
        "macroregion_a":"IF",
        "region":"Paris",
        "region_gid":"whosonfirst:region:85683497",
        "region_a":"VP",
        "localadmin":"Paris",
        "localadmin_gid":"whosonfirst:localadmin:1159322569",
        "locality":"Paris",
        "locality_gid":"whosonfirst:locality:101751119",
        "borough":"13th Arrondissement",
        "borough_gid":"whosonfirst:borough:1158894257",
        "continent":"Europe",
        "continent_gid":"whosonfirst:continent:102191581",
        "label":"175 Rue De Tolbiac, Paris, France"
      }
    }
  ],
  "bbox":[
    2.353198,
    48.825765,
    2.353883,
    48.826171
  ]
}
```

# Isochronie


Le point d'entrée principale est de l'api REST de géocodage/reverse est :

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




