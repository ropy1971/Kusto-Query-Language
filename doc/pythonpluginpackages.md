
* Your own private package
* Different version of existing package


    * Create a blob container to host the package(s), preferably at the same region as your cluster. For example, https://artifcatswestus.blob.core.windows.net/python assuming your cluster is in westus 






    * for private packages: zip the directories of the package and those of its dependencies
4. Upload the zipped file to a blob in the artifacts location
5. Calling the `python` plugin:
    * In your inline python code import `Zipackage` from `sandbox_utils` and call its `install()` method with the name of the zip file
### Example
Installing the [Faker](https://pypi.org/project/Faker/) package that generates fake data:
<!-- csl -->
range Id from 1 to 3 step 1 
| evaluate python(typeof(*),
    'Zipackage.install("Faker.zip")\n'
    'fake = Faker()\n'
    'for i in range(df.shape[0]):\n'
    external_artifacts=pack('faker.zip', 'https://artifacts.blob.core.windows.net/kusto/Faker.zip?...'))

|----|--------------|
|   2| Emma Evans   |
<#endif>