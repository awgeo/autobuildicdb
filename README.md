# autobuildicdb
Download and reformat well data from the NPD, then auto-populate (write directly to) an IC well database.

<b>Introduction</b>

When building a geological well database that covers Norway, we often start with public data from the Norwegian Petroleum Directorate (NPD). The [NPD FactPages](https://factpages.npd.no/en/wellbore) provide tabulated data for some 1900 exploration and 5000 development wells. Starting with Well Header attributes (well location, depth, status, etc.), we download the latest NPD data and begin to populate our database.

Lloyd's Register's [IC software](https://www.lr.org/en-gb/visualise-your-well-data/), formerly ODM (Oilfield Data Manager), allows us to build a regional well database based on SQL Server. In order to prepare the Well Header data for import to IC, we would want to apply a series of transformations to the data that, done in Excel, lack an effective audit trail. The NPD data set is updated regularly as new wells are drilled and data is released, so we should update our well database frequently. This series of Python scripts in Jupyter Notebooks allow us to apply reproducable transformations to the NPD data that allow, for example, for well headers to be updated more regularly and in a consistent format. 

Each subsurface application expects data in a particular format. When importing well headers to IC, for example, you need to match columns/attributes in the file to those default attribute names in the database. To optimise the data files for import, you may wish to rename the attributes in file to match IC's defaults. Also, IC expects Coordinate Grid System to be in the format "ED50 / UTM Zone 31N" and, ideally, a single column will combine Well Status and Content, e.g. "P & A Gas/Condensate". 

The full set of tabulated data provided by the NPD includes: Well Headers Cores, Core photos, Thin sections, CO2, Oil samples, Lithostratigraphy, Drill stem Tests, Casing and leak-off tests and Drilling mud.

Each dataset presents different data management challenges. For example, the depth values of Core Photo are presented in a single column, which we need to split out into three columns: bottom depth, top depth and depth unit. We can then convert all units to metres, to match our IC project configuration. Also, we might want to extract a filename from each Core Photo URL, and check for erroneous data (invalid depths/units, overlapping intervals, repeated depths, etc.)

The main script ('autobuildicdb_NPD_PrepareData.ipynb') outputs reformatted well header files (CSV) that are optimised for import to IC via the relevant import tools, like Import Well Headers and Import Multi-Well ASCII file.

<b>Write directly to the SQL Server database</b>

A second, experimental part to this project ('autobuildicdb_NPD_WriteToDatabase.ipynb') does away with the manual import process altogether, and instead establishes a connection to and writes data directly to the IC SQL Server database. This workflow requires a detailed understanding of the architecture of the IC SQL Server database, and is somewhat convoluted. We are required to write all the data that IC would do during the manual import process. Furthermore, the SQL tables and attributes are named different inside the database to what we see in the IC User Interface. This script is not fully tested. If you want to experiment, use it on a blank IC database and not on an existing populated IC database.

<b>Other scripts (Text Dictionaries, Shapefiles, etc.)</b>

A number of other scripts (work in progress) help build Text Dictionaries based on Lithostratigraphy data, and auto-populate your IC project with NPD Shapefiles. Again, these should be used with caution.

Please get in touch if you'd like to explore any part of this workflow.
