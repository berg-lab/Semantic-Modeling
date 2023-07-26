# Getting Started with Brick
This document will help you in your introduction to Brickschema. It is recommended that you first have an understanding of the material covered in the [Building System Semantic Modeling document](README.md).

## Setup
At this point, Python should be properly set up on your computer. If needed, refer to the [Building System Semantic Modeling document](README.md) for instructions on how to install python. Now, open your IDE and use `pip` to install `brickschema`.

```
pip install brickschema
```
Installation instructions as well as a Quickstart to Brick appear on the [py-brickschema](https://github.com/BrickSchema/py-brickschema) repository.


## Resources
A good starting point to begin to understand Brick concepts, relationships, and models is Brick's [Get Started](https://brickschema.org/get-started/) page. Go through the informational documents and the tutorial slideshows to get an idea of the motivation for Brick and see its uses.

To visualize Brick in action, refer to [BrickStudio](https://brickschema.github.io/brick-studio/), [Brick Viewer](https://brickschema.org/tools/BrickViewer/), or take a look at any of the other resources on the Brick [Tool](https://brickschema.org/tools) page.

Once you are comforable with that material, there is a [Brick Research Reading List](https://home.gtf.fyi/posts/brick-notes/getting-started-brick-research/) that you can look into to work toward doing research with Brick. The reading list was created by Gabe Fierro, a founding member of Brick. He also refers to the W3C documents that were linked in the Building System Semantic Modeling document. However, there are many more links for further research.

## Tutorials
There are many different tutorials and examples that can be used when getting started with Brick. After reading through the resources provided above, going through tutorials should help you understand how that information is being applied.
- As mentioned earlier, the [py-brickschema](https://github.com/BrickSchema/py-brickschema) page has a Quickstart tutorial
- There is a folder of [examples](https://github.com/BrickSchema/Brick/tree/master/examples) in the Brick GitHub repository
  - See [example1](https://github.com/BrickSchema/Brick/blob/master/examples/example1/generate.py) for a detailed step-by-step creation of a Brick model
  - See [simple_apartment](https://github.com/BrickSchema/Brick/blob/master/examples/simple_apartment/generate.py) to learn about zones and spaces
  - Explore the other files in the folder
- The [brick-tutorial-buildingsys2017](https://github.com/BuildSysUniformMetadata/brick-tutorial-buildsys2017) server has tutorials with in-depth descriptions
<br></br>
<div class="warning" style='background-color:#e8faca; color: #769642; border-left: solid #769642 4px; border-radius: 6px; padding:0.7em;'>
<span>
<p style='margin-top:0em; text-align:left'>
<b>:memo:  Tips</b></p>
<p style='margin-left:1em; color: #1b1c1c'> 
<ul>
<li>Make sure that you have downloaded any necessary data files that are loaded in your code</li>
<ul>- You will need to download the <code>Brick.ttl</code> file; see <a href="https://brickschema.org/resources/"> this link</a> to do so</ul>
<li>Make sure to change your directories appropriately when copying-and-pasting code from tutorials</li>
<li>Once you have run through a tutorial and created a <code>.ttl</code> file, you can load this file into TopBraid to explore the RDF graph. Go through the <a href="First-TopBraid-Model.md"> Getting Started with TopBraid</a> document for more information.</li>
</ul>

</div>
