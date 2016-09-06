# SIMD-postcode-search
Basic postcode search to query statistics.gov.scot

The user can enter a postcode to search for its SIMD16 rank from statistics.gov.scot. You can click the Data Zone to find out more about it on statistics.gov.scot.

It uses jQuery to issue a POST to the SPARQL endpoint at statistics.gov.scot, requesting the results as JSON. The results are displayed in a table, which appends additional results to the bottom.

Below is the SPARQL query used. It can be run at statistics.gov.scot/sparql. The postcode "EH1 3DG" is replaced with a variable that picks up the postcode entered by the user.

PREFIX xsd: <http://www.w3.org/2001/XMLSchema#> 
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#> 
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> 
PREFIX qb: <http://purl.org/linked-data/cube#> 
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
 SELECT ?DZ ?Rank 
WHERE {
?s rdf:type <http://data.ordnancesurvey.co.uk/ontology/postcode/PostcodeUnit>.
?s rdfs:label "EH1 3DG".
?s <http://statistics.gov.scot/def/postcode/dataZone2011> ?DZuri.
?DZuri skos:notation ?DZ. ?r <http://purl.org/linked-data/sdmx/2009/dimension#refArea>
?DZuri. ?r qb:dataSet <http://statistics.gov.scot/data/scottish-index-of-multiple-deprivation-2016>.
?r <http://statistics.gov.scot/def/dimension/simdDomain> <http://statistics.gov.scot/def/concept/simd-domain/simd>.
?r <http://purl.org/linked-data/sdmx/2009/dimension#refPeriod> <http://reference.data.gov.uk/id/year/2016>.
?r <http://purl.org/linked-data/cube#measureType> <http://statistics.gov.scot/def/measure-properties/rank>. 
?r <http://statistics.gov.scot/def/measure-properties/rank> ?Rank.
}
