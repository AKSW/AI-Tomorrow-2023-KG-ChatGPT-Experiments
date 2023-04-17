# Foaf + Vcard + Org Ontologies

## Notes

Create relabeled data using:
```
rpt integrate --out-format turtle/pretty foaf-vcard-org-data.ttl relabel-properties-and-classes.rq > relabled-data.ttl
```

## Task 1: Connection Explanation

### ChatGPT 3.5 Mar 23 Version

<details>
<summary>
Given the RDF/Turtle model below, is there any connection between "UK" and "US"?
</summary>
</details>


<details>
<summary>Answer 1/5</summary>
Yes, there is a connection between "UK" and "US" in the RDF/Turtle model provided. The connection is established through the properties vcard:country-name and org:Membership:

1. In the RDF statement :anne vcard:hasAddress [ a vcard:Home ; vcard:country-name "UK" ] ., it is stated that Anne (identified by :anne) has a home address in the UK.
2. In the RDF statement :bob vcard:hasAddress [ a vcard:Home ; vcard:country-name "US" ] ., it is stated that Bob (identified by :bob) has a home address in the US.
3. In the RDF statement [ a org:Membership ; org:member :anne ; org:organization :researchDep ; org:role :chiefResearchOfficer ] ., it is stated that Anne (identified by :anne) is a member of the research department (identified by :researchDep) and holds the role of chief research officer (identified by :chiefResearchOfficer).
4. In the RDF statement [ a org:Membership ; org:member :bob ; org:organization :marketingDep ; org:role :marketingManager ] ., it is stated that Bob (identified by :bob) is a member of the marketing department (identified by :marketingDep) and holds the role of marketing manager (identified by :marketingManager).

So, the connection between "UK" and "US" is indirectly established through the membership of Anne and Bob in the research department and marketing department respectively, as indicated by the org:organization property in the org:Membership statements.
</details>


<details>
<summary>Answer 2/5</summary>
Yes, there is a connection between "UK" and "US" in the RDF/Turtle model provided. The connection is through the vCard ontology, which represents contact information, including addresses, in RDF. Both Anne and Bob are individuals represented as foaf:Person, and they both have addresses represented using vcard:hasAddress property. Anne's address has the country name "UK", while Bob's address has the country name "US". This indicates that Anne's address is in the United Kingdom and Bob's address is in the United States.
</details>


<details>
<summary>Answer 3/5</summary>
Based on the RDF/Turtle model provided, there is no direct connection between "UK" and "US". They are simply values of the property vcard:country-name associated with two different individuals, :anne and :bob, respectively, who are members of different organizations, :researchDep and :marketingDep, respectively, within the overall organization :wonderOrg. The model does not specify any direct relationship or connection between "UK" and "US" beyond this context.
</details>

<details>
<summary>Answer 4/5</summary>
Yes, there is a connection between "UK" and "US" in the given RDF/Turtle model. Specifically, the connection is established through the vcard:country-name property that is associated with the vcard:hasAddress property of the individuals :anne and :bob.

:anne is a member of the :researchDep organizational unit and holds the role of :chiefResearchOfficer in the :wonderOrg organization. The vcard:country-name property associated with the vcard:hasAddress property of :anne indicates that the country associated with her home address is "UK", which stands for the United Kingdom.

Similarly, :bob is a member of the :marketingDep organizational unit and holds the role of :marketingManager in the :wonderOrg organization. The vcard:country-name property associated with the vcard:hasAddress property of :bob indicates that the country associated with his home address is "US", which stands for the United States.
</details>


<details>
<summary>Answer 5/5</summary>
Yes, there is a connection between "UK" and "US" in the RDF/Turtle model. The connection is through the vcard:hasAddress property, which associates the individuals :anne and :bob with their respective addresses. :anne has an address in the "UK" and :bob has an address in the "US".
</details>

### ChatGPT 4 Mar 23 Version

<details>
<summary>Answer 1/5: &check; Correct summarization that both people are member of the same organization.</summary>
No, there is no direct connection between "UK" and "US" in the given RDF/Turtle model. "UK" and "US" are values of the vcard:country-name property, which are assigned to two different individuals, Anne and Bob, respectively. The individuals are members of different organizational units, the research department and the marketing department, respectively, which are both part of the same organization, wonderOrg. However, there is no explicit connection between the two individuals or their respective countries in this model.
</details>

<details>
<summary>Answer 2/5: &cross;</summary>
Based on the RDF/Turtle model provided, there is no direct connection between "UK" and "US".

The model defines two people, Anne and Bob, each with a home address in their respective countries. The model also defines an organization named "wonderOrg" with two departments, a research department and a marketing department. Additionally, the model defines two roles within the organization, a chief research officer and a marketing manager, and assigns Anne and Bob to those roles within their respective departments.

Therefore, there is no explicit or implicit connection between the two countries, UK and US, in this RDF/Turtle model.
</details>

<details>
<summary>Answer 3/5: &cross;</summary>
No, there is no direct connection between "UK" and "US" in the RDF/Turtle model. The only connection between the two is that Anne lives in the UK and Bob lives in the US, but there is no explicit relationship between them or their respective countries in the model.
</details>


<details>
<summary>Answer 4/5: &cross;</summary>
There is no direct connection between "UK" and "US" in the RDF/Turtle model provided. However, there is an implicit connection between "UK" and "Anne Miller" through the vcard:hasAddress property. Similarly, there is an implicit connection between "US" and "Bob Tanner" through the vcard:hasAddress property.
</details>

<details>
<summary>Answer 5/5: &cross; Failed to relate the departments to the same organization.</summary>
Based on the provided RDF/Turtle model, there is no direct connection between "UK" and "US". However, it is possible that there could be an indirect connection between the two through the organization or role memberships.

Anne is a member of the research department and holds the role of Chief Research Officer. Bob is a member of the marketing department and holds the role of Marketing Manager. It is possible that these two departments could have some connection or interaction with each other, which could lead to a connection between UK and US. However, without further information, it is not possible to determine whether there is any such connection between UK and US.
</details>


## Task 2

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

### ChatGPT 4 Mar 23 Version

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


