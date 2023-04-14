# Foaf + Vcard + Org Ontologies


## Task 1

<details>
<summary>
> Given the RDF/Turtle model below, create a SPARQL query that lists for every person the country, company and department and role.
> Please adhere strictly to the given model.
</summary>

```turtle
PREFIX : <https://abc.def/ghi/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX vcard: <http://www.w3.org/2006/vcard/ns#>
PREFIX org: <http://www.w3.org/ns/org#>

:anne a foaf:Person ; foaf:firstName "Anne" ; foaf:surname "Miller" ;
  vcard:hasAddress [ a vcard:Home ; vcard:country-name "UK" ] .
:bob a foaf:Person ; foaf:firstName "Bob" ; foaf:surname "Tanner" ;
  vcard:hasAddress [ a vcard:Home ; vcard:country-name "US" ] .

:wonderOrg a org:Organization .
:researchDep a org:OrganizationalUnit ; org:unitOf :wonderOrg ;
  rdfs:label "Research Department" .
:marketingDep a org:OrganizationalUnit ; org:unitOf :wonderOrg ;
  rdfs:label "Marketing Department" .

:chiefResearchOfficer a org:Role . :marketingManager a org:Role .

[ a org:Membership ; org:member :anne ; org:organization :researchDep ;
  org:role :chiefResearchOfficer ] .
[ a org:Membership ; org:member :bob  ; org:organization :marketingDep ;
  org:role :marketingManager ] .
```
</details>

### ChatGPT 4 ChatGPT Mar 23 Version

<details>
<summary>Answer 1/5: &check;</summary>

Here's a SPARQL query that adheres to the given RDF/Turtle model and lists for every person the country, company, department, and role:

```sparql
PREFIX : <https://abc.def/ghi/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX vcard: <http://www.w3.org/2006/vcard/ns#>
PREFIX org: <http://www.w3.org/ns/org#>

SELECT ?firstName ?surname ?country ?company ?department ?role
WHERE {
  ?person a foaf:Person ;
          foaf:firstName ?firstName ;
          foaf:surname ?surname ;
          vcard:hasAddress [ a vcard:Home ; vcard:country-name ?country ] .

  ?membership a org:Membership ;
              org:member ?person ;
              org:organization ?dep ;
              org:role ?roleObject .

  ?company a org:Organization .
  ?dep org:unitOf ?company ;
       rdfs:label ?department .

  OPTIONAL {
    ?roleObject rdfs:label ?role .
  }
}
```

This query selects the required information for each person, including their first name, surname, country, company, department, and role, based on the given RDF/Turtle model.

</details>

<details>
<summary>Answer 2/5: &cross;</summary>

Here's a SPARQL query that lists for every person the country, company, department, and role, based on the given RDF/Turtle model:

```sparql
SELECT ?person ?firstName ?surname ?country ?company ?department ?role
WHERE {
  ?person a foaf:Person ;
          foaf:firstName ?firstName ;
          foaf:surname ?surname ;
          vcard:hasAddress/vcard:country-name ?country .

  ?membership a org:Membership ;
              org:member ?person ;
              org:organization ?company ;
              org:role ?role .

  ?company a org:Organization ;
           org:hasUnit ?department .

  ?department a org:OrganizationalUnit ;
              org:unitOf ?company .

  ?membership org:organization ?department .
}
```

This query retrieves the person, their first name, surname, country, company, department, and role by matching the relevant triples in the RDF model.

<details>


<details>
<summary>Answer 3/5: &check;</summary>

Here's a SPARQL query that lists for every person the country, company, department, and role, strictly adhering to the given RDF/Turtle model:

```sparql
PREFIX : <https://abc.def/ghi/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX vcard: <http://www.w3.org/2006/vcard/ns#>
PREFIX org: <http://www.w3.org/ns/org#>

SELECT ?person ?firstName ?surname ?country ?company ?department ?role
WHERE {
  ?person a foaf:Person ;
          foaf:firstName ?firstName ;
          foaf:surname ?surname ;
          vcard:hasAddress [ a vcard:Home ; vcard:country-name ?country ] .

  ?membership a org:Membership ;
              org:member ?person ;
              org:organization ?orgUnit ;
              org:role ?roleURI .

  ?orgUnit org:unitOf ?company ;
           rdfs:label ?department .

  OPTIONAL { ?roleURI rdfs:label ?role }
}
```

This query retrieves the person, their first name, surname, country, company, department, and role by matching the appropriate triples in the given RDF/Turtle model. The **``OPTIONAL``** clause is used to account for role URIs that might not have a human-readable label.

<details>


<details>
<summary>Answer 4/5: &cross;</summary>

Here's a SPARQL query that adheres to the given RDF/Turtle model and retrieves the requested information for every person:

```sparql
PREFIX : <https://abc.def/ghi/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX vcard: <http://www.w3.org/2006/vcard/ns#>
PREFIX org: <http://www.w3.org/ns/org#>

SELECT ?firstName ?surname ?countryName ?organizationLabel ?roleLabel
WHERE {
  ?person a foaf:Person ;
          foaf:firstName ?firstName ;
          foaf:surname ?surname ;
          vcard:hasAddress ?address .
  ?address a vcard:Home ;
           vcard:country-name ?countryName .

  ?membership a org:Membership ;
              org:member ?person ;
              org:organization ?organization ;
              org:role ?role .
  ?organization rdfs:label ?organizationLabel .
  ?role rdfs:label ?roleLabel .
}
```

This query will return a list of people, along with their country, company, department, and role.

<details>

<details>
<summary>Answer 5/5: &cross;</summary>

Here is a SPARQL query that lists for every person the country, company, department, and role according to the given RDF/Turtle model:

```sparql
PREFIX : <https://abc.def/ghi/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX vcard: <http://www.w3.org/2006/vcard/ns#>
PREFIX org: <http://www.w3.org/ns/org#>

SELECT ?person ?firstName ?surname ?country ?company ?department ?role WHERE {
  ?person a foaf:Person ;
          foaf:firstName ?firstName ;
          foaf:surname ?surname ;
          vcard:hasAddress ?address .
  ?address a vcard:Home ;
           vcard:country-name ?country .

  ?membership org:member ?person ;
              org:organization ?company ;
              org:role ?roleObject .
  ?company a org:Organization .
  ?roleObject a org:Role ;
              rdfs:label ?role .

  ?department org:unitOf ?company ;
              rdfs:label ?departmentLabel .
  ?membership org:organization ?department .
}```

This query selects the person, first name, surname, country, company, department, and role for each person based on their membership and address information in the RDF/Turtle model.

<details>


