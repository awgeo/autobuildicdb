# autobuildicdb
Download and reformat well data from the NPD then auto-populate an IC well database

<b>Problem</b>

When building a geological well database that covers Norway, we often start with public data from the Norwegian Petroleum Directorate (NPD). The NPD FactPages provide tabulated data for some 1900 exploration and 5000 development wells. Starting with Well Header attributes, we download the latest NPD data and begin to populate our database.

Lloyd's Register's IC software, formerly ODM (Oilfield Data Manager), allows us to build a regional well database (split into projects per Basin or Field, for example) that is based on SQL Server. In order to prepare the Well Header data for import to IC, we would want to apply a series of transformations to the data that, done in Excel, lack an effective audit trail. The NPD data set is updated regularly as new wells and drilled and new and updated data is released, so ideally we should update our well database frequently. This series of Python scripts in Jupyter Notebooks allow us to apply reproducable transformations to the NPD data, allowing, for example, well headers to be updated regularly and in a perfectly consistent format. 

Each subsurface application expects data in a particular format, and some are more flexible than others. When importing well headers to IC, for example, you need to match columns/attributes in the file to those default attribute names in the database. You may wish to rename the attributes in file to match IC's defaults. IC expects Coordinate Reference 



<b>Solution</b>



The full set of tabulated data provided by the NPD includes: Well Headers Cores, Core photos, Thin sections, CO2, Oil samples, Lithostratigraphy, Drill stem Ttsts, Casing and leak-off tests and Drilling mud. 



(NPD) Fact Pages provide tabulated data for all wells with 
all wells with Well header information, Lithostratigraphic itervals, etc. 





History

What started out with well headers has been extended to include Cores, Core photos, Thin sections, CO2, Oil samples, Lithostratigraphy, Drill stem Ttsts, Casing and leak-off tests and Drilling mud.

