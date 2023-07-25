# Building System Semantic Modeling
Semantic modeling, put simply, shows the relationships between data. As it applies to building systems, this means that assets in a building are linked together with relationships. This document provides some resources that may be helpful to someone that is getting started learning about building systems, RDF graphs, Turtle, and other semantic modeling ideas.

## Motivation
To begin to understand the logic and motivation behind building system semantic modeling, there are many websites and videos that can be used. Here are some options...
- [The Power of Digital Twins for Building Automation Operations](https://www.youtube.com/watch?v=JS_SOIoLmGk) is a video that provides a clear description of the vision and capabilities of semantic modeling for building systems.
- The [Johnson Controls](https://www.johnsoncontrols.com/digital-solutions/smart-buildings) website has multiple videos about advancing toward a future with Smart Buildings. Johnson Controls has adopted Brick as a part of their Digital Vault Platform.
- This page on the [TopQuadrant](https://www.topquadrant.com/how-knowledge-graphs-work) website breifly states the advantages of Knowledge Graphs.

## Semantic Modeling Concepts
In order to begin doing work with Brick, TopBraid, BuildingMOTIF, and other modeling tools, it is necessary that you gain an understanding of Resource Description Framework (RDF) graphs and Turtle syntax. Go through these resources to build background knowledge.
- The ["Graph (abstract data type)"](https://en.wikipedia.org/wiki/Graph_(abstract_data_type)) article provides into what a graph refers to in computer science.
- A useful visualization tool is [Brick TTL Viewer](https://viewer.brickschema.org/) which shows the relationsips between instances of Brick classes. By rendering the interactive model, it allows the user to zoom in and out, move around the model, and collapse nodes.
  - You can also refer to [Brick Studio](https://brickschema.github.io/brick-studio/) for the purpose of visualization. This tool allows you to view and edit the graph.
  - Later, you will build a model with TopBraid that will also be a helful visualization tool.

### W3C Resources
W3C has created some documents that are a good place to start. The documents begin with general information and explainations, but proceed to get more specific and syntactic. Take your time as you try to understand the earlier parts. Then, save the rest for later reference.

| Resource | Description |
|---------|-----------|
|[RDF Primer](https://www.w3.org/TR/rdf11-primer/)|This resource explains what RDF is and what is used to create an RDF model.|
|[RDF Turtle](https://www.w3.org/TR/turtle/)|This resource will help with reading Turtle files, which is a common serialization format for RDF graphs.|
|[SPARQL Overview](https://www.w3.org/TR/sparql11-overview/)|This resource explains SPARQL which is the standard query language used for RDF graphs.|
|[SPARQL Query Language](https://www.w3.org/TR/sparql11-query/)|This resource goes into greater detail on how to use SPARQL to read an RDF graph. |
|[Shapes Constraint Language (SHACL)](https://www.w3.org/TR/shacl/)|This resource describes SHACL which is a language used to describe and validate RDF graphs. |

## Understanding Building Systems
ASHRAE has published [Standards and Guidelines](https://www.ashrae.org/technical-resources/ashrae-standards-and-guidelines) that describe uniform methods of testing, recommended practices for design and installation of equipment, and other information to guide the industry. You can likely find pdf documents with this information online. Specifically, when you are working with Brick, it may be helpful to look at ASHRAE Guideline 36 which refers to "High-Performance Sequences of Operation for HVAC Systems".

## Python
For people who are newer to computer science, refer to these sources to set up your computer with Python. After doing so, you will be able to seamlessly use Python to work with Brick and BuildingMOTIF in your IDE.

**Python Installation**
- Visit the [Python Download](https://www.python.org/downloads/) page and click the download Python button to install the latest version. Alternatively, it can also be installed in the Microsoft Store.
- Refer to this [source](https://realpython.com/add-python-to-path/) or find a short video online to add Python to `PATH`

**IDE Setup**
   - [Visual Studio Code](https://code.visualstudio.com/) is one IDE option that is available for download on Windows, Linux and macOS.
     - The [Introductory Videos](https://code.visualstudio.com/docs/getstarted/introvideos) are a good starting point for learning to navigate VS Code
     - There are  documents on [Getting Started with Python in VS Code](https://code.visualstudio.com/docs/python/python-tutorial)
     - Note: You will  need to install the Python extension (see video 5)
<br><br/>
   - Or, another option is [Google Colaboratory](https://colab.google/) which uses notebooks to execute code. Colab can be accessed by web browser.
     - There are many resources for getting started on google colab
       - [GeeksforGeeks article](https://www.geeksforgeeks.org/how-to-use-google-colab/)
       - [neptune.ai blog](https://neptune.ai/blog/google-colab-dealing-with-files
       )
       - [ProgrammingKnowledge video](https://www.youtube.com/watch?v=i-HnvsehuSw)