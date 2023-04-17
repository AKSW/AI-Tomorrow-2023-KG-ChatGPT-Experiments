# Foaf + Vcard + Org Ontologies

## Notes

Create relabeled data using:
```
rpt integrate --out-format turtle/pretty foaf-vcard-org-data.ttl relabel-properties-and-classes.rq > raw-relabled-data.ttl
```
The final file has been manually formatted.

## Task 1A: Connection Explanation

<details>
<summary>Given the RDF/Turtle model below, is there any connection between "UK" and "US"?</summary>

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

**Note: An answer is considered only correct if it mentions that the people are part of the same organization :wonderOrg.**

### ChatGPT 3.5 Mar 23 Version

<details>
<summary>Answer 1/5: &cross;</summary>
Yes, there is a connection between "UK" and "US" in the RDF/Turtle model provided. The connection is established through the properties vcard:country-name and org:Membership:

1. In the RDF statement :anne vcard:hasAddress [ a vcard:Home ; vcard:country-name "UK" ] ., it is stated that Anne (identified by :anne) has a home address in the UK.
2. In the RDF statement :bob vcard:hasAddress [ a vcard:Home ; vcard:country-name "US" ] ., it is stated that Bob (identified by :bob) has a home address in the US.
3. In the RDF statement [ a org:Membership ; org:member :anne ; org:organization :researchDep ; org:role :chiefResearchOfficer ] ., it is stated that Anne (identified by :anne) is a member of the research department (identified by :researchDep) and holds the role of chief research officer (identified by :chiefResearchOfficer).
4. In the RDF statement [ a org:Membership ; org:member :bob ; org:organization :marketingDep ; org:role :marketingManager ] ., it is stated that Bob (identified by :bob) is a member of the marketing department (identified by :marketingDep) and holds the role of marketing manager (identified by :marketingManager).

So, the connection between "UK" and "US" is indirectly established through the membership of Anne and Bob in the research department and marketing department respectively, as indicated by the org:organization property in the org:Membership statements.
</details>


<details>
<summary>Answer 2/5: &cross;</summary>
Yes, there is a connection between "UK" and "US" in the RDF/Turtle model provided. The connection is through the vCard ontology, which represents contact information, including addresses, in RDF. Both Anne and Bob are individuals represented as foaf:Person, and they both have addresses represented using vcard:hasAddress property. Anne's address has the country name "UK", while Bob's address has the country name "US". This indicates that Anne's address is in the United Kingdom and Bob's address is in the United States.
</details>


<details>
<summary>Answer 3/5: &cross;</summary>
Based on the RDF/Turtle model provided, there is no direct connection between "UK" and "US". They are simply values of the property vcard:country-name associated with two different individuals, :anne and :bob, respectively, who are members of different organizations, :researchDep and :marketingDep, respectively, within the overall organization :wonderOrg. The model does not specify any direct relationship or connection between "UK" and "US" beyond this context.
</details>


<details>
<summary>Answer 4/5: &cross;</summary>
Yes, there is a connection between "UK" and "US" in the given RDF/Turtle model. Specifically, the connection is established through the vcard:country-name property that is associated with the vcard:hasAddress property of the individuals :anne and :bob.

:anne is a member of the :researchDep organizational unit and holds the role of :chiefResearchOfficer in the :wonderOrg organization. The vcard:country-name property associated with the vcard:hasAddress property of :anne indicates that the country associated with her home address is "UK", which stands for the United Kingdom.

Similarly, :bob is a member of the :marketingDep organizational unit and holds the role of :marketingManager in the :wonderOrg organization. The vcard:country-name property associated with the vcard:hasAddress property of :bob indicates that the country associated with his home address is "US", which stands for the United States.
</details>


<details>
<summary>Answer 5/5; &cross;</summary>
Yes, there is a connection between "UK" and "US" in the RDF/Turtle model. The connection is through the vcard:hasAddress property, which associates the individuals :anne and :bob with their respective addresses. :anne has an address in the "UK" and :bob has an address in the "US".
</details>

### ChatGPT 4 Mar 23 Version

<details>
<summary>Answer 1/5: &check; Correct summarization that both people are member of the same organization.</summary>
Based on the RDF/Turtle model provided, there is no explicit connection between "UK" and "US." However, there is an indirect connection between "UK" and "US" through the people who live in these countries and their roles in the organization.

Anne lives in the "UK" and is the chief research officer of the Research Department, which is a part of the "wonderOrg" organization. Bob lives in the "US" and is the marketing manager of the Marketing Department, which is also a part of the "wonderOrg" organization.

So, while there is no direct connection between "UK" and "US" in the model, there is an indirect connection through the people (Anne and Bob) and their roles in the same organization.
</details>


<details>
<summary>Answer 2/5: &check;</summary>
Based on the RDF/Turtle model provided, there is an indirect connection between "UK" and "US" through the people who are associated with an organization called "wonderOrg". Anne is from the "UK" and is a member of the Research Department within "wonderOrg", holding the role of Chief Research Officer. On the other hand, Bob is from the "US" and is a member of the Marketing Department within the same organization, holding the role of Marketing Manager. While there is no direct connection between "UK" and "US" in the model, the two countries are connected through the people who work in different departments of "wonderOrg".
</details>


<details>
<summary>Answer 3/5: &check;</summary>
In the given RDF/Turtle model, there is no direct connection between "UK" and "US." However, there is an indirect connection between the two through the individuals Anne and Bob, who are from the UK and the US, respectively. Both of them are members of different organizational units within the same organization, :wonderOrg. Anne is a member of the :researchDep and has the role of :chiefResearchOfficer, while Bob is a member of the :marketingDep and has the role of :marketingManager.
</details>


<details>
<summary>Answer 4/5: &check;</summary>
Based on the RDF/Turtle model provided, there is an indirect connection between "UK" and "US" through the organization structure and the people who are part of it.

Anne and Bob have addresses in the "UK" and "US," respectively. Both of them are members of the same organization, ":wonderOrg," in different departments:

* Anne is a member of the ":researchDep" (Research Department) and has the role of ":chiefResearchOfficer."
* Bob is a member of the ":marketingDep" (Marketing Department) and has the role of ":marketingManager."

So, while there isn't a direct connection between "UK" and "US" in the RDF/Turtle model, there is an indirect connection through Anne and Bob's membership in the same organization, ":wonderOrg," while they reside in different countries.
</details>

<details>
<summary>Answer 5/5: &check;</summary>
Based on the RDF/Turtle model provided, there is an indirect connection between "UK" and "US" through the shared organization, :wonderOrg.

Anne, who lives in the "UK", is a member of the :researchDep, which is a part of :wonderOrg. On the other hand, Bob, who lives in the "US", is a member of the :marketingDep, also a part of :wonderOrg. While there is no direct connection between the "UK" and "US" in this model, both Anne and Bob are connected through their roles in the same organization, :wonderOrg.
</details>


## Task 1B
Same as 1A but with a relabled model.

<details>
<summary>Given the RDF/Turtle model below, is there any connection between "UK" and "US"?</summary>

```turtle
PREFIX eg:  <http://www.example.org/>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX : <https://abc.def/ghi/>

:anne a eg:class5 ; eg:prop12  "Anne" ; eg:prop13  "Miller" ;
  eg:prop14  [ a eg:class0 ; eg:prop9  "UK" ] .
:bob a eg:class5 ; eg:prop12  "Bob" ; eg:prop13  "Tanner" ;
  eg:prop14  [ a eg:class0 ; eg:prop9  "US" ] .

:wonderOrg a eg:class3 .
:researchDep a eg:class1  ; eg:prop10 :wonderOrg ;
  eg:prop11 "Research Department" .
:marketingDep a eg:class1 ; eg:prop10 :wonderOrg ;
  eg:prop11 "Marketing Department" .

:chiefResearchOfficer a eg:class4 . :marketingManager a eg:class4 .

[ a eg:class2 ; eg:prop6 :anne ; eg:prop7 :researchDep ;
  eg:prop8 :chiefResearchOfficer ] .
[ a eg:class2 ; eg:prop6 :bob  ; eg:prop7 :marketingDep ;
  eg:prop8 :marketingManager ] .
```

</details>



### ChatGPT 4 Mar 23 Version
<details>
<summary>Answer 1/5: &cross;</summary>
Based on the given RDF/Turtle model, there is no explicit connection between "UK" and "US". They are only related in the sense that they are values of the property eg:prop9 for two different individuals, :anne and :bob. In the model, :anne has a connection to the "UK" and :bob has a connection to the "US". However, there is no direct connection or relationship between the "UK" and the "US" mentioned within this model.
</details>

<details>
<summary>Answer 2/5: &check;</summary>
In the given RDF/Turtle model, there is an indirect connection between "UK" and "US". The connection can be understood through the individuals :anne and :bob.

:anne is associated with "UK" through the property eg:prop14:

```turtle
:anne a eg:class5 ; eg:prop12  "Anne" ; eg:prop13  "Miller" ;
  eg:prop14  [ a eg:class0 ; eg:prop9  "UK" ] .

:bob is associated with "US" through the property eg:prop14:
```

```turtle
:bob a eg:class5 ; eg:prop12  "Bob" ; eg:prop13  "Tanner" ;
  eg:prop14  [ a eg:class0 ; eg:prop9  "US" ] .
```

Both :anne and :bob are individuals of eg:class5 and are related to different departments within :wonderOrg, with :anne being related to the :researchDep and :bob being related to the :marketingDep. Although there is no direct connection between "UK" and "US", the connection is established through the individuals and their roles within the organization.
</details>

<details>
<summary>Answer 3/5: &check;</summary>
n the given RDF/Turtle model, the connection between "UK" and "US" can be inferred through the individuals ":anne" and ":bob", who are associated with the countries "UK" and "US" respectively through the property eg:prop9.

:anne has the property eg:prop14 with the value "UK".
:bob has the property eg:prop14 with the value "US".

Although there is no direct connection between "UK" and "US" in the RDF/Turtle model, the connection can be made indirectly through the individuals ":anne" and ":bob" who belong to the same class eg:class5 and are associated with different departments within the same organization :wonderOrg.
</details>

<details>
<summary>Answer 4/5: &check;</summary>
Based on the RDF/Turtle model provided, there is no explicit connection between "UK" and "US". However, there is an implicit connection between "UK" and "US" in the sense that both are related to different individuals in the dataset.

The individual "Anne" has a property (eg:prop14) with a value of "UK", while the individual "Bob" has the same property (eg:prop14) with a value of "US". Both Anne and Bob are instances of the same class (eg:class5) and have relationships with different departments in the organization.

While there is no direct connection between "UK" and "US" in this model, the indirect connection exists through the individuals and their properties in the dataset.
</details>

<details>
<summary>Answer 5/5: &cross;</summary>
n the given RDF/Turtle model, there is an indirect connection between "UK" and "US" through the individuals Anne and Bob. Anne is associated with the "UK" via the property eg:prop14, and Bob is associated with the "US" via the same property.

To be more specific, the connection is as follows:

Anne (eg:prop14) -> UK
Bob (eg:prop14) -> US

Although the connection is not direct, both Anne and Bob are connected to their respective countries through the same property (eg:prop14), which implies a connection between "UK" and "US" in the context of this model.
</details>


## Task 2

<details>
<summary>Given the RDF/Turtle model below, create a SPARQL query that lists for every person the country, company and department and role. Please adhere strictly to the given model.</summary>

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


## Task3: Standardize Classes and Properties

<details>
<summary>Given the RDF/Turtle model below, please replace all properties and classes with the most likely standard ones.</summary>

```turtle
PREFIX eg:  <http://www.example.org/>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX : <https://abc.def/ghi/>

:anne a eg:class5 ; eg:prop12  "Anne" ; eg:prop13  "Miller" ;
  eg:prop14  [ a eg:class0 ; eg:prop9  "UK" ] .
:bob a eg:class5 ; eg:prop12  "Bob" ; eg:prop13  "Tanner" ;
  eg:prop14  [ a eg:class0 ; eg:prop9  "US" ] .

:wonderOrg a eg:class3 .
:researchDep a eg:class1  ; eg:prop10 :wonderOrg ;
  eg:prop11 "Research Department" .
:marketingDep a eg:class1 ; eg:prop10 :wonderOrg ;
  eg:prop11 "Marketing Department" .

:chiefResearchOfficer a eg:class4 . :marketingManager a eg:class4 .

[ a eg:class2 ; eg:prop6 :anne ; eg:prop7 :researchDep ;
  eg:prop8 :chiefResearchOfficer ] .
[ a eg:class2 ; eg:prop6 :bob  ; eg:prop7 :marketingDep ;
  eg:prop8 :marketingManager ] .
```

</details>


### ChatGPT 4 Mar 23 Version

**TODO** Need some degree of correctness - syntactically correct, use of all correct vocabs, use of plausible properties.

<details>
<summary>Answer 1/5: &cross; &cross; &cross; Overall very good; use of foaf:name for departments suboptimal</summary>
Here's the RDF/Turtle model with the properties and classes replaced with more standard ones:

```turtle
PREFIX foaf: http://xmlns.com/foaf/0.1/
PREFIX rdf: http://www.w3.org/1999/02/22-rdf-syntax-ns#
PREFIX xsd: http://www.w3.org/2001/XMLSchema#
PREFIX org: http://www.w3.org/ns/org#
PREFIX vcard: http://www.w3.org/2006/vcard/ns#
PREFIX : https://abc.def/ghi/

:anne a foaf:Person ;
foaf:givenName "Anne" ;
foaf:familyName "Miller" ;
vcard:hasAddress [ a vcard:Address ; vcard:country-name "UK" ] .
:bob a foaf:Person ;
foaf:givenName "Bob" ;
foaf:familyName "Tanner" ;
vcard:hasAddress [ a vcard:Address ; vcard:country-name "US" ] .

:wonderOrg a org:Organization .
:researchDep a org:OrganizationalUnit ;
org:subOrganizationOf :wonderOrg ;
foaf:name "Research Department" .
:marketingDep a org:OrganizationalUnit ;
org:subOrganizationOf :wonderOrg ;
foaf:name "Marketing Department" .

:chiefResearchOfficer a org:Role .
:marketingManager a org:Role .

[ a org:Membership ;
org:member :anne ;
org:organization :researchDep ;
org:role :chiefResearchOfficer ] .
[ a org:Membership ;
org:member :bob ;
org:organization :marketingDep ;
org:role :marketingManager ] .
```

</details>


<details>
<summary>Answer 2/5: &cross;</summary>
I have replaced the custom classes and properties with more standard ones from widely-used vocabularies, such as FOAF, schema.org, and Dublin Core.

```turtle
PREFIX foaf: http://xmlns.com/foaf/0.1/
PREFIX rdf: http://www.w3.org/1999/02/22-rdf-syntax-ns#
PREFIX xsd: http://www.w3.org/2001/XMLSchema#
PREFIX schema: http://schema.org/
PREFIX dc: http://purl.org/dc/terms/
PREFIX : https://abc.def/ghi/

:anne a foaf:Person ;
foaf:givenName "Anne" ;
foaf:familyName "Miller" ;
schema:address [ a schema:PostalAddress ; schema:addressCountry "UK" ] .
:bob a foaf:Person ;
foaf:givenName "Bob" ;
foaf:familyName "Tanner" ;
schema:address [ a schema:PostalAddress ; schema:addressCountry "US" ] .

:wonderOrg a schema:Organization .
:researchDep a schema:Organization ;
schema:parentOrganization :wonderOrg ;
dc:title "Research Department" .
:marketingDep a schema:Organization ;
schema:parentOrganization :wonderOrg ;
dc:title "Marketing Department" .

:chiefResearchOfficer a schema:JobTitle .
:marketingManager a schema:JobTitle .

[ a schema:EmployeeRole ;
schema:employee :anne ;
schema:memberOf :researchDep ;
schema:jobTitle :chiefResearchOfficer ] .
[ a schema:EmployeeRole ;
schema:employee :bob ;
schema:memberOf :marketingDep ;
schema:jobTitle :marketingManager ] .
```
</details>


<details>
<summary>Answer 3/5: &cross;</summary>

```turtle
PREFIX eg: http://www.example.org/
PREFIX rdf: http://www.w3.org/1999/02/22-rdf-syntax-ns#
PREFIX xsd: http://www.w3.org/2001/XMLSchema#
PREFIX : https://abc.def/ghi/
PREFIX foaf: http://xmlns.com/foaf/0.1/
PREFIX org: http://www.w3.org/ns/org#
PREFIX vcard: http://www.w3.org/2006/vcard/ns#

:anne a foaf:Person ;
foaf:givenName "Anne" ;
foaf:familyName "Miller" ;
vcard:hasAddress [ a vcard:Address ; vcard:country-name "UK" ] .
:bob a foaf:Person ;
foaf:givenName "Bob" ;
foaf:familyName "Tanner" ;
vcard:hasAddress [ a vcard:Address ; vcard:country-name "US" ] .

:wonderOrg a org:Organization .
:researchDep a org:OrganizationalUnit ;
org:subOrganizationOf :wonderOrg ;
foaf:name "Research Department" .
:marketingDep a org:OrganizationalUnit ;
org:subOrganizationOf :wonderOrg ;
foaf:name "Marketing Department" .

:chiefResearchOfficer a org:Role .
:marketingManager a org:Role .

[ a org:Membership ;
org:member :anne ;
org:organization :researchDep ;
org:role :chiefResearchOfficer ] .
[ a org:Membership ;
org:member :bob ;
org:organization :marketingDep ;
org:role :marketingManager ] .

```
</details>


<details>
<summary>Answer 4/5: &cross;</summary>

In order to replace the properties and classes with the most likely standard ones, I'll use the following namespaces and standard classes/properties:

* foaf: http://xmlns.com/foaf/0.1/
* vcard: http://www.w3.org/2006/vcard/ns#
* org: http://www.w3.org/ns/org#

Here's the updated RDF/Turtle model:

```turtle
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX : <https://abc.def/ghi/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX vcard: <http://www.w3.org/2006/vcard/ns#>
PREFIX org: <http://www.w3.org/ns/org#>

:anne a foaf:Person;
  foaf:givenName "Anne";
  foaf:familyName "Miller";
  vcard:hasAddress [ a vcard:Address;
    vcard:country-name "UK" ] .

:bob a foaf:Person;
  foaf:givenName "Bob";
  foaf:familyName "Tanner";
  vcard:hasAddress [ a vcard:Address;
    vcard:country-name "US" ] .

:wonderOrg a org:Organization .

:researchDep a org:OrganizationalUnit;
  org:subOrganizationOf :wonderOrg;
  foaf:name "Research Department" .

:marketingDep a org:OrganizationalUnit;
  org:subOrganizationOf :wonderOrg;
  foaf:name "Marketing Department" .

:chiefResearchOfficer a foaf:Role .
:marketingManager a foaf:Role .

[ a org:Membership;
  org:member :anne;
  org:organization :researchDep;
  org:role :chiefResearchOfficer ] .

[ a org:Membership;
  org:member :bob;
  org:organization :marketingDep;
  org:role :marketingManager ] .

```
In this updated model, I have used the FOAF (Friend of a Friend) vocabulary to describe people, the vCard ontology for addressing, and the W3C Organization ontology to describe organizations, organizational units, and memberships.
</details>


<details>
<summary>Answer 5/5: &cross;</summary>
Here is the RDF/Turtle model with properties and classes replaced with the most likely standard ones:

```turtle
PREFIX foaf: http://xmlns.com/foaf/0.1/
PREFIX rdf: http://www.w3.org/1999/02/22-rdf-syntax-ns#
PREFIX xsd: http://www.w3.org/2001/XMLSchema#
PREFIX org: http://www.w3.org/ns/org#
PREFIX vcard: http://www.w3.org/2006/vcard/ns#
PREFIX : https://abc.def/ghi/

:anne a foaf:Person ;
foaf:givenName "Anne" ;
foaf:familyName "Miller" ;
vcard:hasAddress [ a vcard:Address ; vcard:country-name "UK" ] .
:bob a foaf:Person ;
foaf:givenName "Bob" ;
foaf:familyName "Tanner" ;
vcard:hasAddress [ a vcard:Address ; vcard:country-name "US" ] .

:wonderOrg a org:Organization .
:researchDep a org:FormalOrganization ;
org:subOrganizationOf :wonderOrg ;
foaf:name "Research Department" .
:marketingDep a org:FormalOrganization ;
org:subOrganizationOf :wonderOrg ;
foaf:name "Marketing Department" .

:chiefResearchOfficer a foaf:Role .
:marketingManager a foaf:Role .

[ a org:Membership ;
org:member :anne ;
org:organization :researchDep ;
org:role :chiefResearchOfficer ] .
[ a org:Membership ;
org:member :bob ;
org:organization :marketingDep ;
org:role :marketingManager ] .

```

</details>


### ChatGPT 3.5 Mar 23 Version


<details>
<summary>Answer 1/5: &check; Foaf and Org ontology not used, but still a plausible best effort result</summary>

```turtle
PREFIX eg: http://www.example.org/
PREFIX rdf: http://www.w3.org/1999/02/22-rdf-syntax-ns#
PREFIX xsd: http://www.w3.org/2001/XMLSchema#
PREFIX : https://abc.def/ghi/

:anne a eg:Person ; eg:firstName "Anne" ; eg:lastName "Miller" ;
eg:location [ a eg:Country ; eg:countryName "UK" ] .
:bob a eg:Person ; eg:firstName "Bob" ; eg:lastName "Tanner" ;
eg:location [ a eg:Country ; eg:countryName "US" ] .

:wonderOrg a eg:Organization .
:researchDep a eg:Department ; eg:belongsTo :wonderOrg ;
eg:departmentName "Research Department" .
:marketingDep a eg:Department ; eg:belongsTo :wonderOrg ;
eg:departmentName "Marketing Department" .

:chiefResearchOfficer a eg:Employee . :marketingManager a eg:Employee .

[ a eg:JobRole ; eg:employee :anne ; eg:department :researchDep ;
eg:supervisor :chiefResearchOfficer ] .
[ a eg:JobRole ; eg:employee :bob ; eg:department :marketingDep ;
eg:supervisor :marketingManager ] .
```

</details>

<details>
<summary>Answer 2/5: &check; Foaf and Org ontology not used, but still a plausible best effort result</summary>

```turtle
PREFIX eg: http://www.example.org/
PREFIX rdf: http://www.w3.org/1999/02/22-rdf-syntax-ns#
PREFIX xsd: http://www.w3.org/2001/XMLSchema#
PREFIX : https://abc.def/ghi/

:anne rdf:type eg:Person ; eg:firstName "Anne" ; eg:lastName "Miller" ;
eg:location [ rdf:type eg:Country ; eg:countryName "UK" ] .
:bob rdf:type eg:Person ; eg:firstName "Bob" ; eg:lastName "Tanner" ;
eg:location [ rdf:type eg:Country ; eg:countryName "US" ] .

:wonderOrg rdf:type eg:Organization .
:researchDep rdf:type eg:Department ; eg:belongsTo :wonderOrg ;
eg:departmentName "Research Department" .
:marketingDep rdf:type eg:Department ; eg:belongsTo :wonderOrg ;
eg:departmentName "Marketing Department" .

:chiefResearchOfficer rdf:type eg:Executive .
:marketingManager rdf:type eg:Executive .

[ rdf:type eg:Employment ; eg:employee :anne ; eg:department :researchDep ;
eg:position :chiefResearchOfficer ] .
[ rdf:type eg:Employment ; eg:employee :bob ; eg:department :marketingDep ;
eg:position :marketingManager ] .
```

</details>

<details>
<summary>Answer 3/5: &cross; Several classes and properties not replaced.</summary>

```turtle
PREFIX eg: http://www.example.org/
PREFIX rdf: http://www.w3.org/1999/02/22-rdf-syntax-ns#
PREFIX xsd: http://www.w3.org/2001/XMLSchema#
PREFIX : https://abc.def/ghi/

:anne a rdf:Class5 ; eg:prop12 "Anne" ; eg:prop13 "Miller" ;
eg:prop14 [ a rdf:Class0 ; eg:prop9 "UK" ] .
:bob a rdf:Class5 ; eg:prop12 "Bob" ; eg:prop13 "Tanner" ;
eg:prop14 [ a rdf:Class0 ; eg:prop9 "US" ] .

:wonderOrg a rdf:Class3 .
:researchDep a rdf:Class1 ; eg:prop10 :wonderOrg ;
eg:prop11 "Research Department" .
:marketingDep a rdf:Class1 ; eg:prop10 :wonderOrg ;
eg:prop11 "Marketing Department" .

:chiefResearchOfficer a rdf:Class4 . :marketingManager a rdf:Class4 .

[ a rdf:Class2 ; eg:prop6 :anne ; eg:prop7 :researchDep ;
eg:prop8 :chiefResearchOfficer ] .
[ a rdf:Class2 ; eg:prop6 :bob ; eg:prop7 :marketingDep ;
eg:prop8 :marketingManager ] .
```

</details>

<details>
<summary>Answer 4/5: &cross; Several classes and properties not replaced.</summary>

```turtle
PREFIX eg: http://www.example.org/
PREFIX rdf: http://www.w3.org/1999/02/22-rdf-syntax-ns#
PREFIX xsd: http://www.w3.org/2001/XMLSchema#
PREFIX : https://abc.def/ghi/

:anne a rdf:Class5 ; eg:prop12 "Anne" ; eg:prop13 "Miller" ;
eg:prop14 [ a rdf:Class0 ; eg:prop9 "UK" ] .
:bob a rdf:Class5 ; eg:prop12 "Bob" ; eg:prop13 "Tanner" ;
eg:prop14 [ a rdf:Class0 ; eg:prop9 "US" ] .

:wonderOrg a rdf:Class3 .
:researchDep a rdf:Class1 ; eg:prop10 :wonderOrg ;
eg:prop11 "Research Department" .
:marketingDep a rdf:Class1 ; eg:prop10 :wonderOrg ;
eg:prop11 "Marketing Department" .

:chiefResearchOfficer a rdf:Class4 . :marketingManager a rdf:Class4 .

[ a rdf:Class2 ; eg:prop6 :anne ; eg:prop7 :researchDep ;
eg:prop8 :chiefResearchOfficer ] .
[ a rdf:Class2 ; eg:prop6 :bob ; eg:prop7 :marketingDep ;
eg:prop8 :marketingManager ] .
```

</details>

<details>
<summary>Answer 5/5: &cross; Several classes and properties not replaced.</summary>

```turtle
PREFIX eg: http://www.example.org/
PREFIX rdf: http://www.w3.org/1999/02/22-rdf-syntax-ns#
PREFIX xsd: http://www.w3.org/2001/XMLSchema#
PREFIX : https://abc.def/ghi/

:anne a rdf:Class5 ; eg:prop12 "Anne" ; eg:prop13 "Miller" ;
eg:prop14 [ a rdf:Class0 ; eg:prop9 "UK" ] .
:bob a rdf:Class5 ; eg:prop12 "Bob" ; eg:prop13 "Tanner" ;
eg:prop14 [ a rdf:Class0 ; eg:prop9 "US" ] .

:wonderOrg a rdf:Class3 .
:researchDep a rdf:Class1 ; eg:prop10 :wonderOrg ;
eg:prop11 "Research Department" .
:marketingDep a rdf:Class1 ; eg:prop10 :wonderOrg ;
eg:prop11 "Marketing Department" .

:chiefResearchOfficer a rdf:Class4 . :marketingManager a rdf:Class4 .

[ a rdf:Class2 ; eg:prop6 :anne ; eg:prop7 :researchDep ;
eg:prop8 :chiefResearchOfficer ] .
[ a rdf:Class2 ; eg:prop6 :bob ; eg:prop7 :marketingDep ;
eg:prop8 :marketingManager ] .
```

</details>
