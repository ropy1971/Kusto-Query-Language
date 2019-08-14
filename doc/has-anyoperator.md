


```
```
**Syntax**
*T* `|` `where` *col* `has_any` `(`*list of scalar expressions*`)`   
 

* *col* - Column to filter.
* *tabular expression* - Tabular expression that has a set of values (if expression has multiple columns, the first column is used)
**Returns**
Rows in *T* for which the predicate is `true`
**Notes**
* The expression list can produce up to `10,000` values.    



```
| where State has_any ("CAROLINA", "DAKOTA", "NEW") 
```
|State|count_|
|NEW YORK|1750|
|SOUTH DAKOTA|1567|
|SOUTH CAROLINA|915|
|NEW MEXICO|527|

**Using dynamic array:**
<!-- csl: https://help.kusto.windows.net/Samples -->
let states = dynamic(['south', 'north']);
| where State has_any (states)
```
|State|count_|
|NORTH CAROLINA|1721|
|SOUTH CAROLINA|915|
|ATLANTIC SOUTH|193|