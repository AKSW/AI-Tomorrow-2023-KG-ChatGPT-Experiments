# Tests on Mondial Knowledge Graph

## Task: create SPARQL query


### Prompt:
```
pease create a sparql query based on the mondial knowledgegraph for the following question:
which river has the most riparian states?
```

<details>
<summary>best practice solution</summary>

```SPARQL
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix mondial: <http://www.semwebtech.org/mondial/10/meta#>

SELECT ?river (COUNT(?country) AS ?count)
WHERE {
  ?river rdf:type mondial:River .
  ?river mondial:locatedIn ?country .
  ?country rdf:type mondial:Country .
}
GROUP BY ?river
ORDER BY DESC(?count)
LIMIT 1
```

#### correct answer:
| river | count |
| ------|-------|
| `<http://www.semwebtech.org/mondial/10/rivers/Donau/>` | `"10"^^<http://www.w3.org/2001/XMLSchema#integer>` |

checked with https://www.semwebtech.org/mondial/10/sparql

</details>


### ChatGPT 3.5 Mar 23 Version
5 Answers via "regenerate" from GPT-3.5 (default)

<details>
<summary>Answer 1/5: &cross;</summary>

```sparql
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

#### comments on 1/5
* &check; syntax correct
* &cross; query structure with unnecessary complexity: usage of subquery, binding for `?source` and `?sourceCountry` never used
* &cross; wrong mondial namespace, correct would be http://www.semwebtech.org/mondial/10/meta#
* &cross; wrong usage of property `mondial:flowsThrough` (country does not fit to range `mondial:Lake`, better would be `mondial:locatedIn`
* &cross; undefined property used: `mondial:hasRiparianState`, `mondial:hasMouth` and `mondial:hasRiparianState` are not defined
* &cross; query result: 0 records

</details>

<details>
<summary>Answer 2/5: &cross;</summary>

```sparql
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

#### comments on 2/5
* &check; syntax correct
* &check; plausible query structure
* &cross; wrong mondial namespace, correct would be http://www.semwebtech.org/mondial/10/meta#
* &cross; wrong usage of property `mondial:flowsThrough` (country does not fit to range `mondial:Lake`, better would be `mondial:locatedIn`
* &check; usage of defined properties & classes
* &cross; query result: 0 records

</details>

<details>
<summary>Answer 3/5: &cross;</summary>

```sparql
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

#### comments for 3/5
* &check; syntax correct
* &cross; query structure with unnecessary complexity: strange usage of subquery, duplicate connection between river and country via `mondial:flowsThrough` and `mondial:isRiparian`
* &cross; wrong mondial namespace, correct would be http://www.semwebtech.org/mondial/10/meta#
* &cross; wrong usage of property `mondial:flowsThrough` (country does not fit to range `mondial:Lake`, better would be `mondial:locatedIn`
* &cross; undefined property used: `mondial:isRiparian` is not defined
* &cross; query result: 0 records
</details>

<details>
<summary>Answer 4/5: &cross;</summary>

```sparql
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

#### comments for 4/5
* &check; syntax correct
* &cross; bad query structure with unbound `?riverName`
* &cross; wrong mondial namespace, correct would be http://www.semwebtech.org/mondial/10/meta#
* &cross; wrong usage of property `mondial:flowsThrough` (state does not fit to range `mondial:Lake`, better would be `mondial:locatedIn`
* &cross; undefined class used: `mondial:State` is not defined, better would be `mondial:Country`
* &cross; query result: 0 records
</details>

<details>
<summary>Answer 5/5: &cross;</summary>

```sparql
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

#### comments for 5/5
* &check; syntax correct
* &check; plausible query structure, but duplicate connection between `?river` and `?country`
* &cross; wrong mondial namespace, correct would be http://www.semwebtech.org/mondial/10/meta#
* &cross; wrong usage of property `mondial:flowsThrough` (country does not fit to range `mondial:Lake`, better would be `mondial:locatedIn`
* &cross; undefined property used: `mondial:isRiparian` is not defined
* &cross; query result: 0 records
</details>



### ChatGPT 4 Mar 23 Version
5 Answers from GPT-4 via "regenerate answer":

<details>
<summary>Answer 1/5: &cross;</summary>

```sparql
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

#### comments for 1/5
* &check; syntax correct
* &check; plausible query structure, but prefix `xsd` never used
* &check; correct mondial namespace
* &cross; wrong usage of property `rdfs:label` for river, mondial uses (untypically) `mondial:name`
* &cross; undefined class used: `mondial:State` is not defined
* &cross; query result: 0 records
</details>

<details>
<summary>Answer 2/5: &cross;</summary>

```sparql
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

#### comments for 2/5
* &check; syntax correct
* &cross; query structure not based on mondial knowledge graph
* ? mondial namespace not used
* &cross; query result: 0 records
</details>

<details>
<summary>Answer 3/5: &cross;</summary>

```sparql
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

#### comments for 3/5
* &check; syntax correct
* &check; plausible query structure, type of `?state` not defined
* &cross; wrong mondial namespace, correct would be http://www.semwebtech.org/mondial/10/meta#
* &cross; wrong usage of property `rdfs:label` for river, mondial uses (untypically) `mondial:name`
* &check; usage of defined properties & classes
* &cross; query result: 0 records
</details>

<details>
<summary>Answer 4/5: &cross;</summary>

```sparql
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

#### comments for 4/5
* &check; syntax correct
* &check; plausible query structure, but prefix `geo` never used
* &cross; wrong mondial namespace, correct would be http://www.semwebtech.org/mondial/10/meta#
* &cross; wrong usage of property `mondial:flowsThrough` (country does not fit to range `mondial:Lake`, better would be `mondial:locatedIn`
* &check; usage of defined properties & classes
* &cross; query result: 0 records
</details>

<details>
<summary>Answer 5/5: &cross;</summary>

```sparql
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

#### comments for 5/5
* &check; syntax correct
* &check; plausible query structure, but prefix `xsd` never used
* &cross; wrong mondial namespace, correct would be http://www.semwebtech.org/mondial/10/meta#
* &cross; wrong usage of property `mondial:flowsThrough` (country does not fit to range `mondial:Lake`, better would be `mondial:locatedIn`
* &check; usage of defined properties & classes
* &cross; query result: 0 records
