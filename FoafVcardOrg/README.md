# Foaf + Vcard + Org Ontologies


## Task 1

<details>
<summary>
Given the RDF/Turtle model below, create a SPARQL query that lists for every person the country, company and department and role. Please adhere strictly to the given model.
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

</details>


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

</details>


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

</details>


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
}
```

This query selects the person, first name, surname, country, company, department, and role for each person based on their membership and address information in the RDF/Turtle model.

</details>


### ChatGPT 3.5 Mar 23 Version

<details>
<summary>Answer 1/5: &cross; but yields {person,ountry}</summary>

Here's the SPARQL query that lists the country, company, department, and role for every person:

```sparql
PREFIX : <https://abc.def/ghi/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX vcard: <http://www.w3.org/2006/vcard/ns#>
PREFIX org: <http://www.w3.org/ns/org#>

SELECT ?person ?country ?company ?department ?role
WHERE {
  ?person a foaf:Person ;
         foaf:firstName ?firstName ;
         foaf:surname ?surname ;
         vcard:hasAddress [ a vcard:Home ;
                            vcard:country-name ?country ] .
  OPTIONAL {
    ?membership org:member ?person ;
                org:organization ?org ;
                org:role ?role .
    ?org a org:Organization ;
         (org:unitOf|org:subOrganization)* ?company ;
         rdfs:label ?department .
  }
}
```

This query first selects all the individuals that are instances of foaf:Person and retrieves their first name, surname, and country from the vcard:hasAddress property. Then, it uses the OPTIONAL keyword to retrieve the organization, department, and role information for each person, if available. The (org:unitOf|org:subOrganization)* part in the query allows for retrieving the organization that the department is a part of, recursively. The retrieved results will contain the person, country, company, department, and role for every person in the RDF/Turtle model.

</details>


<details>
<summary>Answer 2/5: &check;</summary>

Here's the SPARQL query that lists the country, company, department, and role for every person:

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
         vcard:hasAddress/vcard:country-name ?country .

  ?membership org:member ?person ;
              org:role ?role ;
              org:organization ?department .

  ?department a org:OrganizationalUnit ;
              rdfs:label ?departmentLabel ;
              org:unitOf ?company .

  ?company a org:Organization .
}
```

This query retrieves the first name and surname of each person, as well as the country from their address. It then retrieves the membership information for each person, including the role and department they belong to. Finally, it retrieves the label of the department and the organization it belongs to. The results will include the first name, surname, country, company, department, and role for every person in the RDF/Turtle model.

</details>


<details>
<summary>Answer 3/5: &check;</summary>

The SPARQL query to list the country, company, department, and role for every person based on the given RDF/Turtle model is:

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
         vcard:hasAddress [ a vcard:Home ;
                            vcard:country-name ?country ] .
  ?membership a org:Membership ;
             org:member ?person ;
             org:role ?role ;
             org:organization ?org .
  ?org a org:OrganizationalUnit ;
       org:unitOf ?company ;
       rdfs:label ?department .
  ?company a org:Organization .
}
```

This query retrieves the first name, surname, country, company, department, and role of each person in the RDF/Turtle model. It uses SPARQL triple patterns to match the relevant properties and classes in the RDF data. The ?person variable represents a person, and the ?org variable represents an organizational unit. The query also uses the ?company variable to represent the organization that the department is a unit of. The results will be displayed as a table with columns for first name, surname, country, company, department, and role.
</details>


<details>
<summary>Answer 4/5: &cross; (only yields person IRI and country)</summary>

Here's a SPARQL query that retrieves the country, company, department, and role for every person:

```sparql
PREFIX : <https://abc.def/ghi/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX vcard: <http://www.w3.org/2006/vcard/ns#>
PREFIX org: <http://www.w3.org/ns/org#>

SELECT ?person ?country ?company ?department ?role
WHERE {
  ?person a foaf:Person ;
          foaf:firstName ?firstName ;
          foaf:surname ?surname ;
          vcard:hasAddress [ a vcard:Home ;
                             vcard:country-name ?country ] .
  OPTIONAL {
    ?membership org:member ?person ;
                org:organization ?department ;
                org:role ?role .
    ?department a org:OrganizationalUnit ;
                rdfs:label ?departmentLabel .
    ?organization org:hasMember ?person ;
                  rdfs:label ?company .
  }
}
```

This query retrieves the ?person, ?country, ?company, ?department, and ?role for every person. It uses the OPTIONAL keyword to retrieve information about the organization, department, and role only if it exists for a particular person. The FOAF and vCard prefixes are used to retrieve the first name, surname, and country of the person, while the org prefix is used to retrieve information about the organization, department, and role.

</details>


<details>
<summary>Answer 5/5: &check;</summary>

Here's a SPARQL query that lists the country, company, department, and role for every person:

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
         vcard:hasAddress [ vcard:country-name ?country ] .

  ?membership org:member ?person ;
              org:role ?role ;
              org:organization ?department .

  ?department org:unitOf ?org ;
              rdfs:label ?company .

  ?org a org:Organization .
}
```

This query uses SPARQL's SELECT statement to retrieve the desired information for every person. It uses the foaf:Person class and the foaf:firstName, foaf:surname, and vcard:hasAddress properties to get the person's first name, surname, and country respectively. It also uses the org:Membership class, along with the org:member, org:role, and org:organization properties to get the person's role, department, and company information. Finally, it uses the org:unitOf property to link the department to its parent organization.
</details>


