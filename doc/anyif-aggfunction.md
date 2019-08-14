


(e.g., an "error text" column) and you want to sample that column once per a unique value of the compound group key.

> There are *no guarantees* about which record will be returned; the algorithm for selecting that record is undocumented and one should not assume it is stable.
**Syntax**
`summarize` `anyif(`*Expr*, `*Predicate*`)`
**Arguments**
* *Expr*: Expression that will be used for aggregation calculation.



**Examples**
Show random continent which has a population from 300 million to 600 million:
<!-- csl -->
Continents | summarize anyif(Continent, Population between (300000000 .. 600000000))
