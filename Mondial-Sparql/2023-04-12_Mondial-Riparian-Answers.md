Prompt:
pease create a sparql query based on the mondial knowledgegraph for the following question:
which river has the most riparian states?


5 Answers via "regenerate" from GPT-3.5 (default)
```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX mondial: <http://www.semwebtech.org/mondial/10/schema#>

SELECT ?river ?numRiparianStates
WHERE {
  ?river rdf:type mondial:River .
  ?river mondial:flowsThrough ?country .
  ?country mondial:isLocatedIn ?continent .
  ?river mondial:hasSource ?source .
  ?source mondial:isLocatedIn ?sourceCountry .
  ?river mondial:hasMouth ?mouth .
  ?mouth mondial:isLocatedIn ?mouthCountry .
  ?river mondial:hasRiparianState ?riparianState .
  
  {
    SELECT ?river (COUNT(DISTINCT ?riparianState) AS ?numRiparianStates)
    WHERE {
      ?river mondial:hasRiparianState ?riparianState .
    }
    GROUP BY ?river
    ORDER BY DESC(?numRiparianStates)
    LIMIT 1
  }
}
```

```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX mondial: <http://www.semwebtech.org/mondial/10/schema#>

SELECT ?riverName (COUNT(DISTINCT ?country) as ?numRiparianStates)
WHERE {
    ?river rdf:type mondial:River .
    ?river mondial:flowsThrough ?country .
    ?country rdf:type mondial:Country .
}
GROUP BY ?riverName
ORDER BY DESC(?numRiparianStates)
LIMIT 1
```

```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX mondial: <http://www.semwebtech.org/mondial/10/schema#>

SELECT ?river ?count
WHERE {
  ?river rdf:type mondial:River .
  ?river mondial:flowsThrough ?country .
  ?country mondial:isRiparian ?river .
  
  {
    SELECT ?river (COUNT(DISTINCT ?country) AS ?count)
    WHERE {
      ?river rdf:type mondial:River .
      ?river mondial:flowsThrough ?country .
      ?country mondial:isRiparian ?river .
    }
    GROUP BY ?river
    ORDER BY DESC(?count)
    LIMIT 1
  }
}
```

```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX mondial: <http://www.semwebtech.org/mondial/10/schema#>

SELECT ?riverName (COUNT(DISTINCT ?state) AS ?numRiparianStates)
WHERE {
  ?river rdf:type mondial:River .
  ?river mondial:flowsThrough ?state .
  ?state rdf:type mondial:State .
}
GROUP BY ?riverName
ORDER BY DESC(?numRiparianStates)
LIMIT 1
```

```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX mondial: <http://www.semwebtech.org/mondial/10/schema#>

SELECT ?riverName (COUNT(?country) AS ?count)
WHERE {
  ?river rdf:type mondial:River .
  ?river mondial:flowsThrough ?country .
  ?country mondial:isRiparian ?river .
  ?river mondial:name ?riverName .
} 
GROUP BY ?riverName 
ORDER BY DESC(?count)
LIMIT 1
```


5 Answers from GPT-4 via "regenerate answer":
```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX geo: <http://www.telegraphis.net/ontology/geography/geography#>
PREFIX mondial: <http://www.semwebtech.org/mondial/10/meta#>

SELECT ?river ?riverName (COUNT(?state) AS ?stateCount)
WHERE {
  ?river rdf:type geo:River .
  ?river rdfs:label ?riverName .
  ?state rdf:type mondial:State .
  ?river geo:passesThrough ?state .
}
GROUP BY ?river ?riverName
ORDER BY DESC(?stateCount)
LIMIT 1
```

```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX geo: <http://telegraphis.net/ontology/geography/geography#>
PREFIX dbpedia: <http://dbpedia.org/resource/>

SELECT ?riverName (COUNT(?state) AS ?stateCount)
WHERE {
  ?river rdf:type geo:River .
  ?river rdfs:label ?riverName .
  ?state rdf:type geo:Country .
  ?river geo:flowsThrough ?state .
}
GROUP BY ?riverName
ORDER BY DESC(?stateCount)
LIMIT 1
```

```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX geo: <http://www.telegraphis.net/ontology/geography/geography#>
PREFIX mon: <http://www.telegraphis.net/ontology/mondial/mondial-entities#>

SELECT ?river ?riverName (COUNT(?state) AS ?numberOfStates)
WHERE {
    ?river rdf:type mon:River .
    ?river rdfs:label ?riverName .
    ?river geo:passesThrough ?state .
}
GROUP BY ?river ?riverName
ORDER BY DESC(?numberOfStates)
LIMIT 1

```

```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX geo: <http://www.telegraphis.net/ontology/geography/geography#>
PREFIX mondial: <http://www.semwebtech.org/mondial/10/2012/mondial.owl#>

SELECT ?river (COUNT(?state) AS ?stateCount) WHERE {
  ?river rdf:type mondial:River .
  ?state rdf:type mondial:Country .
  ?river mondial:flowsThrough ?state .
} GROUP BY ?river
ORDER BY DESC(?stateCount)
LIMIT 1
```

```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX mondial: <http://www.semwebtech.org/mondial/2005/mondial.owl#>

SELECT ?river ?riverName (COUNT(?state) as ?numStates)
WHERE {
  ?river rdf:type mondial:River .
  ?river rdfs:label ?riverName .
  ?river mondial:flowsThrough ?state .
  ?state rdf:type mondial:Country .
}
GROUP BY ?river ?riverName
ORDER BY DESC(?numStates)
LIMIT 1

```