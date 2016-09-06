# SIMD-postcode-search
Basic postcode search to query statistics.gov.scot

The user can enter a postcode to search for its SIMD16 rank from statistics.gov.scot. You can click the Data Zone to find out more about it on statistics.gov.scot.

It uses jQuery to issue a POST to the SPARQL endpoint at statistics.gov.scot, requesting the results as JSON. The results are displayed in a table, which appends additional results to the bottom.

The SPARQL query used is in the file "SIMDbot SPARQL query.sparql". It can be run at statistics.gov.scot/sparql. The postcode "EH1 3DG" is replaced with a variable that picks up the postcode entered by the user.
