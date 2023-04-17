# Token counts for common knowledge graphs


| example | type | token count | file size |
|--|--|--|--|
| schema.ttl from schema.org | turtle | 150,000 token| 433,522 Byte |
| DBpedia rdf schema | nt | 1,780,799 token | 4,898,168 Byte |
| DBpedia rdf schema | turtle| 471,251 token | 1,454,891 Byte |
| DBpedia rdf schema | xml/rdf | 2,338,484 token| 7,212,677 Byte |
| mondial oracle db schema | sql schema | 2,608 token | 10,709 Byte |
| mondial rdf schema | n3 | 5,369 token | 18,465 Byte |
| mondial rdf schema | nt | 5,369 token | 102,810 Byte |
| mondial rdf schema | turtle| 5,339 token | 19,596 Byte |
| mondial rdf schema | xml/rdf | 17,179 token| 58,703 Byte |
| mondial rdf schema | functional syntax | 9,696 token | 36,520 Byte |
| mondial rdf schema | manchester syntax | 11,336 token | 38,936 Byte |
| Pizza Ontology | xml/rdf | 35,331 token | 117,207 Byte |
| Wine Ontology | xml/rdf | 24,217 token | 78,225 Byte |

### sources used:  

m: Mondial database from https://www.dbis.informatik.uni-goettingen.de/Mondial  
s: Schema graph from https://github.com/schemaorg/schemaorg/blob/main/data/schema.ttl  
p: Pizza Ontology from https://protege.stanford.edu/ontologies/pizza/pizza.owl  
w: Wine Ontology from https://www.w3.org/TR/2003/PR-owl-guide-20031215/wine

### Remarks

* we converted to turtle with rapper from https://librdf.org/raptor/
* we  converted  to  manchester  and  functional  syntax  with  the  help  of  
https://www.ldf.fi/service/owl-converter/
* Calculated by https://github.com/Kibubu/paper-infai-data-kg-and-chatgpt
