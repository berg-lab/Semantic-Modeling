# Real World Model
This document provides some information about how Building System Semantic Modeling is being applied and tested in the real world. It is recommended that you understand the core concepts that are applied in semantic modeling before reading this. Refer to the [Building System Semantic Modeling document](README.md) for that necessary background information.

## Introduction to IBAL
The Intelligent Buildings Agents Laboratory (IBAL) was designed by researchers at the National Institute of Standards and Technology for development and testing of building optimization technologies. It consists of zones and equipment that would exist in a comercial building to mimic that space. For futher reading, visit this [website](https://www.nist.gov/el/energy-and-environment-division-73200/intelligent-buildings-agents-project/ibal-overview), or to view a tour of the lab, see this [video](https://www.nist.gov/video/tour-intelligent-building-agents-laboratory).

## Understanding the Model

#### Schematic
To gain an understanding of the RDF graph, it is helpful to first visualize what is models by looking at the [schematic](https://drive.google.com/drive/search?q=IBAL) (if the image appears blurry, download the file). It is color coded and labeled with the same naming pattern that is found in the RDF graph. Junctions are red, segments are pink, and equipment is green and blue. The entire schematic has 38 junctions that are all connected to various types of equipment including motorized dampers, AHUs, VAVs, valves, and more. A sample screenshop of junction 14 was taken and is displayed below. Note the segments and equipment that is surrounding the junction. This will be consistent with the RDF graph.

![Schematic Sample](Jnc14-Schematic.png)

#### RDF Graph
Throughout the enire model, segments are used to link junctions and eqipment. There is a cnx relationship between each segment and either the inlet or outlet connection point of the corresponding junction/equipment that is found in the schematic. It is not possible for the connection point of two junctions/equipments to have a direct cnx relationship to each other. The segment is required to serve as the connection between the two. Directionality is achieved as the connection points are distinguished between inlet and outlet. To ensure that the model is logical, it must be the case that a connection is attached to one inlet and one outlet connection point. Otherwise, there would be air/glycol flowing into the equipment and not leaving or flowing out with no supply. 

Refering to the sample discussed earlier, junction 14 is connected to Motorized Damper 13, Motorized Damper 14, and AHU 2, as it was expected to be based on the schematic. What is not visible in the graph is the connections and connection points that exist. Junction 14 has two inlet connection points and one outlet connection point. The first inlet connection point has a cnx relationship with Segment 41 which connects it to motorized damper 13. The second inlet connection point has a cnx relationship with Segment 40 which connects it to motorized damper 14. Finally, the outlet connection point has a cnx relationship with Segment 42 which connects it to AHU 2.

![RDF Sample](Jnc14-RDF.png)

All of this information about the connections to equipment and other junctions can be obseved for each of the 38 junctions. The RDF graph creats a web that links every aspect of the laboratory. Starting at any given point on the graph, it can be expanded futher and futher to observe all that is shown in the full schematic.