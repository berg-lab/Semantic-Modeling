# Getting Started with BuildingMOTIF
This document shows how to successfully build, validate, and correct a BuildingMOTIF model. Additionally, it shows how to write, save, and organize templates in BuildingMOTIF. It is recommended that you first have an understanding of the material covered in the [Building System Semantic Modeling document](README.md).

## Installation Instructions

1. Make sure that [Python >= 3.8.0](https://www.python.org/downloads/) has been installed

2. Make sure that [Poetry >= 1.4.0 ](https://python-poetry.org/docs/#installing-with-the-official-installer) has been installed
3. Clone the [BuildingMOTIF](https://github.com/NREL/BuildingMOTIF) Repository: For more information on cloning the repository in Visual Studio Code, refer to [Working with GitHub in VS Code](https://code.visualstudio.com/docs/sourcecontrol/github)

4. Use `pip` to install `buildingmotif` by running the below line in the terminal
```
pip install buildingmotif
```


## Tutorials
Once the above installation has been completed, the following four tutorials should run without any issues. If you are having issues with the tutorials, make sure that Poetry was installed properly.
___
### Model Creation
The [Model Creation](https://nrel.github.io/BuildingMOTIF/tutorials/model_creation.html) tutorial walks the user through the process of creating a Brick model. Then, it shows how to use BuildingMOTIF to load libraries, add to the model manually, and add to the model using a template.

**Tip:** Throughout the tutorials, pay attention to the warning messages that appear along the right side of the page. The code will need to be adjusted accordingly.


<div class="warning" style='background-color:#caddfc; color: #326abf; border-left: solid #326abf 4px; border-radius: 6px; padding:0.7em;'>
<span>
<p style='margin-top:0em; text-align:left'>
<b>:heavy_check_mark: More Practice</b></p>
<p style='margin-left:1em; color: #1b1c1c'> Try writing Python code to add a Brick <code>Air_Flow_Setpoint</code> to this model. Then, connect it to the AHU.</p>

<details>
  <summary><b>Click here to reveal the solution</b></summary>

  ```py
#get Air_Flow_Setpoint template
air_flow_setpt_template = brick.get_template_by_name(BRICK.Air_Flow_Setpoint)

#add Air_Flow_Setpoint
air_flow_setpt_name = f"{ahu_name}-Air_Flow_Setpoint"
air_flow_setpt_binding = {"name": BLDG[air_flow_setpt_name]}
air_flow_setpt_graph = air_flow_setpt_template.evaluate(air_flow_setpt_binding)
model.add_graph(air_flow_setpt_graph)

#connect the Air_Flow_Setpoint to AHU
model.graph.add((BLDG[ahu_name], BRICK.hasPart, BLDG[air_flow_setpt_name]))
  ```
</p></span>
</div>
</details>

___
### Model Validation
The [Model Validation](https://nrel.github.io/BuildingMOTIF/tutorials/model_validation.html) tutorial demonstrates how BuildingMOTIF uses SHACL to check that the model uses Brick correctly and contains the required metadata. 

**WARNING...** In the sections titled "Fixing the Model" and "Validating the Model", it states that model is expected to be valid. This will not be the case with the given code. Instead, it will show the below statement, which explains that it needs a supply fan. This will be corrected in the next tutorial.
```
Model is invalid for these reasons: - urn:bldg/Core_ZN-PSC_AC needs between 1 and 1 instances of urn:ashrae/g36/4.8/sz-vav-ahu/sa-fan on path https://brickschema.org/schema/Brick#hasPart  
PS C:\Users\1sama\Desktop\BuildingMOTIF>
```
<div class="warning" style='background-color:#caddfc; color: #326abf; border-left: solid #326abf 4px; border-radius: 6px; padding:0.7em;'>
<span>
<p style='margin-top:0em; text-align:left'>
<b>:heavy_check_mark: More Practice</b></p>
<p style='margin-left:1em; color: #1b1c1c'> Try writing a shape that requires the model to have a Brick <code>Air_Flow_Setpoint</code>.

<details>
  <summary><b>Click here to reveal the solution</b></summary>

  ```py
  :air-flow-setpoint-count a sh:NodeShape ;
    sh:message "need 1 air flow setpoint" ;
    sh:targetNode : ;
    constraint:exactCount 1 ;
    constraint:class brick:Air_Flow_Setpoint .
  ```
  <p style='margin-left:1em; color: #1b1c1c'> Now, try going back to the Python file that was created when executing the Model Creation tutorial. Comment out the additional practice <code>Air_Flow_Setpoint</code>. Then, go to the Python file with the Model Validation tutorial, and run it again. If the shape requiring the <code>Air_Flow_Setpoint</code> is working correctly, the terminal will show the following... </p>

  ```py
  - Graph did not have 1 instances of https://brickschema.org/schema/Brick#Air_Flow_Setpoint
  ```
  <p style='margin-left:1em; color: #1b1c1c'> This means that you have successfully added the constraint!
</p></span>
</div>
</details>

___
### Model Correction
The [Model Correction](https://nrel.github.io/BuildingMOTIF/tutorials/model_correction.html) tutorial shows how an invalid model can be automatically corrected by using templates.

**Note:** The needed supply fan from the previous warning has been added.

___
### Template Writing
The [Template Writing](https://nrel.github.io/BuildingMOTIF/tutorials/template_writing.html) tutorial exlains that a template is able to generate parts of an RDF model to fix a validation issue. The tutorial walks through the parts of a template as well as how to save and organize templates. 

**Note:** Once you have created the YAML template file, you may have issues running the code to save and organize the templates. For issues such as the following...

```
buildingmotif.building_motif.singleton.SingletonNotInstantiatedException
```
```
Exception: Directory ..\..\my-templates does not exist
```
Complete these steps:
1. Make sure that the template is saved in a `.yml` file (not a `.yaml` file). 
2.
   ```py
   # necessary import statements
   from rdflib import Namespace, Graph
   from buildingmotif import BuildingMOTIF
   from buildingmotif.dataclasses import Model, Library
   ```

3.
   ```py
   # (in a python file) load the template library as follows:
   # 1. create the BuildingMOTIF instance
   bm = BuildingMOTIF("sqlite://") # in-memory
   # 2. load dependencies and load the library from the directory
   _ = Library.load(ontology_graph="./libraries/brick/Brick-subset.ttl")
   lib = Library.load(directory="./my-templates")
   # the name of the library will be name of the directory
   print(f"Loaded library named {lib.name}")
   ```
4. ```py
   # now we can traverse the library to see what's there
   for template in lib.get_templates():
      print(f"Template '{template.name}' has parameters {template.parameters}")
      print("The body of the template looks like this:")
      print(template.body.serialize(format='turtle'))
   ```
Based on the BuildingMOTIF tutorial, this should produce the below code as an expected output.
```
Loaded library named my-templates
Template 'vav-terminal-reheat' has parameters {'za-temp', 'co2', 'zone', 'damper', 'name', 'sa-temp', 'occ', 'sa-flow', 'htg-coil'}
The body of the template looks like this:
@prefix brick: <https://brickschema.org/schema/Brick#> .

<urn:___param___#name> a brick:Variable_Air_Volume_Box_With_Reheat ;
    brick:feeds <urn:___param___#zone> ;
    brick:hasPart <urn:___param___#damper>,
        <urn:___param___#htg-coil> ;
    brick:hasPoint <urn:___param___#co2>,
        <urn:___param___#occ>,
        <urn:___param___#sa-flow>,
        <urn:___param___#sa-temp>,
        <urn:___param___#za-temp> .


Template 'damper' has parameters {'dmppos', 'name'}
The body of the template looks like this:
@prefix brick: <https://brickschema.org/schema/Brick#> .

<urn:___param___#name> a brick:Damper ;
    brick:hasPoint <urn:___param___#dmppos> .


Template 'htg-coil' has parameters {'name', 'cmd'}
The body of the template looks like this:
@prefix brick: <https://brickschema.org/schema/Brick#> .

<urn:___param___#name> a brick:Heating_Coil ;
    brick:hasPoint <urn:___param___#cmd> .
```

**More Resources:** Visit the [notebooks folder](https://github.com/NREL/BuildingMOTIF/tree/develop/notebooks) in the BuildingMOTIF GitHub Repository for more information. There are instructions on writing, evaluating, and using templates.
