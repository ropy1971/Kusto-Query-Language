




  Null values produce null values, and the next value starts a new session.

  The maximum distance between the current value of *Expr* and the value of
  It is a scalar constant of type `timespan`.
* *MaxDistanceBetweenNeighbors* establishes a second criterion for starting a new session:
  It is a scalar constant of type `timespan`.
* *Restart* is an optional scalar expression of type `boolean`. If specified,







   the previous value of *Expr*.
The condition the determines if the value represents a new session is


  *MaxDistanceFromFirst*.
* If the value of *Expr* equals to or exceeds the previous value of *Expr*


with two columns, an `ID` column which identifies a sequence, and a `Timestamp`
a session can't exceed 1 hour, and it continues as long as records are less than

```
    // ...
| sort by ID asc, Timestamp asc
```