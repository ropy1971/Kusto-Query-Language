





* *rotate_count*: Integer specifying the number of positions that array elements will be rotated to the left. If the value is negative, the elements will be rotated to the right.
**Returns**
Dynamic array containing the same amount of the elements as in original array, where each element was rotated according to *rotate_count*.
**See also**
* For rotating array to the right, see [array_rotate_right()](array_rotate_rightfunction.md).
* For shifting array to the right, see [array_shift_right()](array_shift_rightfunction.md).
**Examples**
* Rotating to the left by two positions:
    <!-- csl: https://help.kusto.windows.net:443/Samples -->
    print arr=dynamic([1,2,3,4,5]) 
    ```
    |arr|arr_rotated|
    |[1,2,3,4,5]|[3,4,5,1,2]|
* Rotating to the right by two positions by using negative rotate_count value:
    <!-- csl: https://help.kusto.windows.net:443/Samples -->
    print arr=dynamic([1,2,3,4,5]) 
    ```
    |arr|arr_rotated|
    |[1,2,3,4,5]|[4,5,1,2,3]|