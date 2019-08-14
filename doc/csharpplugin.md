
### Syntax


    * The format is: `typeof(`*ColumnName*`:` *ColumnType* [, ...]`)`, for example: `typeof(col1:string, col2:long)`.
* *script*: A `string` literal that is the valid C# script to be executed.
   C# script as a property bag (see [C# variables](#csharp-interface)).
   Default: `single`.
    * `per_node`: If the query before the C# block is distributed, an instance of the script will run on each node over the data that it contains.
### CSharp interface
The C# script can include any number of classes and methods, but must implement a method with the following signature:
```c#
{
``` 
Where:
* `input`: The input tabular data (the values of `T` above), as an `IEnumerable<TInput>`.
        * For example: if the input schema is `(a:string, b:bool: c:dynamic)`, then `TInput` will be:
        ```c#
        {
            public Boolean? @b;
        }


    string GetArgument(string argumentName);
    T GetArgument<T>(string argumentName, Func<string, T> conversionFunction);

            any Kusto query operator that follows the plugin.
    * `TOutput` is an automatically generated C# class, which is based on the output schema for the plugin (as defined in *output_schema*).

        public class TOutput
            public Int32? @a;
        }



    * *Interested in enabling the plugin on your cluster?*


* The C# sandbox limits accessing the network, therefore the C# code can't dynamically install additional packages that are
### Examples
<!-- csl -->
range x from 1 to 360 step 1
| evaluate csharp(
    'IEnumerable<TOutput> Process(IEnumerable<TInput> input, ICSharpSandboxContext context)' //  The C# decorated script
    '    var n = context.GetArgument("count", int.Parse);'
    '    var f = context.GetArgument("cycles", int.Parse);'
    '    foreach (var row in input) '
    '       yield return new TOutput { x = row.x, fx = MyCalculator.Calculate(g, n, f, row.x) };'
    '}'
    'public static class MyCalculator'
    '    public static double Calculate(int g, int n, int f, long? value)'
    '        return value.HasValue ? g * Math.Sin((double)value / n * 2 * Math.PI * f) : 0.0;'
    '}',
)
```
![alt text](./images/samples/sine-demo.png "sine-demo")
### Performance tips
* Reduce the plugin's input data set to the minimum amount required (columns/rows).
    * To perform a calculation on a subset of the source columns, project only those column before invoking the plugin.
    * You can also use the [partition operator](partitionoperator.md) for partitioning the input data set.


    ```
    | where StartedOn > ago(7d) // Filtering out irrelevant records before invoking the plugin
    | evaluate hint.distribution = per_node csharp( // Using per_node distribution, as the script's logic allows it
        'IEnumerable<TOutput> Process(IEnumerable<TInput> input, ICSharpSandboxContext context)' //  The C# decorated script
        '    foreach (var row in input) '
        '       yield return new TOutput { d = row.d, d2 = 2 * row.d };'  // Negative example: this logic should have been written using Kusto's query language
        '}'
    ```
### Usage tips
* To avoid conflicts between Kusto string delimiters and C# ones, we recommend using single quote characters (`'`) for Kusto string 

  a script that you've stored in an external location, such as Azure blob storage, a public GitHub repository, etc.
  For example:
    <!-- csl -->
    let script = 
        [h'https://raw.githubusercontent.com/yonileibowitz/kusto.blog/master/resources/csharp/sample_script.cs']
    range x from 1 to 360 step 1
        typeof(*, fx:double),
        pack('gain', 100, 'cycles', 4, 'count', toscalar(T | count)))
    ```
* One can run the plugin in `debug` mode, in order to to get the auto-generated code as a string literal.

    ```
    | evaluate csharp(typeof(c_bool:bool), 'debug')


    IEnumerable<TOutput> Process(IEnumerable<TInput> input, ICSharpSandboxContext context)
    }
    public class TInput
        public String @c_string;
        public TimeSpan? @c_timespan;
        public Decimal? @c_decimal;

    {
    }
<#endif>