







* *Predicate*: predicate that if true, the *Expr* calculated value will be checked for minimum.
**Returns**
The minimum value of *Expr* across the group for which *Predicate* evaluates to `true`.
**Examples**
<!-- csl -->
range x from 1 to 100 step 1
```
|minif_x|
|51|