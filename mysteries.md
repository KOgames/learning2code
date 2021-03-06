# About
This file collects things I stumbled upon and did not fully grasp, at least not at first sight.

# Python
* [::](https://docs.python.org/release/2.3.5/whatsnew/section-slices.html) ("stepping slices")
* The philosophical differences between Python 2 and 3, and their practical implications as to whether a given piece of code from one will work in the other or not, and why

# SPARQL syntax
* [.](https://data-gov.tw.rpi.edu/wiki/How_to_use_SPARQL#Query_syntax)
* [p:](https://query.wikidata.org/#select%20%3Fitem%20%3Fseriesordinal%20%3Fauthoritem%20where%20%7B%0A%20%20%3Fitem%20p%3AP2093%20%3Fauthorstring%20.%0A%20%20%3Fitem%20p%3AP50%20%3Fauthoritem%20.%0A%20%20%3Fauthoritem%20pq%3AP1545%20%3Fseriesordinal%20.%0A%20%20%3Fauthorstring%20pq%3AP1545%20%3Fseriesordinal%20.%0A%7D) (as opposed to "wdt:")
* [ps:](https://www.wikidata.org/wiki/Wikidata:SPARQL_query_service/queries/examples#Number_of_handed_out_academy_awards_per_award_type)
* [pq:](https://www.wikidata.org/wiki/Wikidata:SPARQL_query_service/queries/examples#Number_of_handed_out_academy_awards_per_award_type)
* [|](https://query.wikidata.org/#SELECT%20%3Fcity%20%3FcityLabel%20%28MAX%28%3Finhabitants%29%20AS%20%3Finhabitants%29%20WHERE%20%7B%0A%20%3Fcity%20%28p%3AP31%2Fps%3AP31%29%2Fwdt%3AP279%2a%20wd%3AQ1637706.%0A%20MINUS%20%7B%20%3Finhabitant%20ps%3AP19%7Cps%3AP551%7Cps%3AP20%20%3Fcity.%20%7D%0A%20OPTIONAL%20%7B%20%3Fcity%20wdt%3AP1082%20%3Finhabitants.%20%7D%0A%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22.%20%7D%0A%7D%0AGROUP%20BY%20%3Fcity%20%3FcityLabel)
* [\*](https://query.wikidata.org/#SELECT%20%3Fcity%20%3FcityLabel%20%28MAX%28%3Finhabitants%29%20AS%20%3Finhabitants%29%20WHERE%20%7B%0A%20%3Fcity%20%28p%3AP31%2Fps%3AP31%29%2Fwdt%3AP279%2a%20wd%3AQ1637706.%0A%20MINUS%20%7B%20%3Finhabitant%20ps%3AP19%7Cps%3AP551%7Cps%3AP20%20%3Fcity.%20%7D%0A%20OPTIONAL%20%7B%20%3Fcity%20wdt%3AP1082%20%3Finhabitants.%20%7D%0A%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22.%20%7D%0A%7D%0AGROUP%20BY%20%3Fcity%20%3FcityLabel)
* [/](https://query.wikidata.org/#SELECT%20%3Fcity%20%3FcityLabel%20%28MAX%28%3Finhabitants%29%20AS%20%3Finhabitants%29%20WHERE%20%7B%0A%20%3Fcity%20%28p%3AP31%2Fps%3AP31%29%2Fwdt%3AP279%2a%20wd%3AQ1637706.%0A%20MINUS%20%7B%20%3Finhabitant%20ps%3AP19%7Cps%3AP551%7Cps%3AP20%20%3Fcity.%20%7D%0A%20OPTIONAL%20%7B%20%3Fcity%20wdt%3AP1082%20%3Finhabitants.%20%7D%0A%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22.%20%7D%0A%7D%0AGROUP%20BY%20%3Fcity%20%3FcityLabel)
* [\[\]](https://query.wikidata.org/#SELECT%20%3Fcause%20%3FcauseLabel%20%28COUNT%28%3Fperson%29%20AS%20%3Fcount%29%0AWHERE%0A%7B%0A%20%20%3Fperson%20wdt%3AP31%20wd%3AQ5%3B%0A%20%20%20%20%20%20%20%20%20%20wdt%3AP509%20%3Fcause%3B%0A%20%20%20%20%20%20%20%20%20%20wdt%3AP53%20%5B%5D.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22.%20%7D%0A%7D%0AGROUP%20BY%20%3Fcause%20%3FcauseLabel%0AHAVING%28%3Fcount%20%3E%201%29%0AORDER%20BY%20DESC%28%3Fcount%29)

# SPARQL queries that did not work for me (at least not as expected)
* [duplicate series ordinal (P1545) for author string (P2093) statements](https://query.wikidata.org/#select%20%3Fitem%20%3Fseriesordinal%20where%20%7B%0A%20%20%3Fitem%20p%3AP50%20%3Fauthorstring%20%3B%0A%20%20%20%20%20%20%20%20p%3AP50%20%3Fauthorstring2%20.%0A%20%20%3Fauthorstring%20pq%3AP1545%20%3Fseriesordinal%20.%0A%20%20%3Fauthorstring2%20pq%3AP1545%20%3Fseriesordinal%20.%0A%7D)
  - [a similar query, with similar issues](https://query.wikidata.org/#select%20%3Fitem%20%3Fseriesordinal%20%3Fauthoritem%20where%20%7B%0A%20%20%3Fitem%20p%3AP2093%20%3Fauthorstring%20.%0A%20%20%3Fitem%20p%3AP50%20%3Fauthoritem%20.%0A%20%20%3Fauthoritem%20pq%3AP1545%20%3Fseriesordinal%20.%0A%20%20%3Fauthorstring%20pq%3AP1545%20%3Fseriesordinal%20.%0A%7D)
