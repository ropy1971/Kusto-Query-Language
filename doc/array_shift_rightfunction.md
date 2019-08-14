





* *shift_count*: Integer specifying the number of positions that array elements will be shifted to the right. If the value is negative, the elements will be shifted to the left.




* For rotating array right, see [array_rotate_right()](array_rotate_rightfunction.md).



    ```
    | extend arr_shift=array_shift_right(arr, 2)
    
    |---|---|


    ```
    | extend arr_shift=array_shift_right(arr, 2, -1)
    
    |---|---|

* Shifting to the left by two positions by using a negative shift_count value:
    <!-- csl: https://help.kusto.windows.net:443/Samples -->
    print arr=dynamic([1,2,3,4,5]) 
    ```
    |arr|arr_shift|
    |[1,2,3,4,5]|[3,4,5,-1,-1]|