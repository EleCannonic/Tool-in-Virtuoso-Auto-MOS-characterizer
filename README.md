# Auto MOS Characterizer in Virtuoso

This document describes how to use Auto MOS Characterizer in Cadence Virtuoso. It covers starting the tool with `load("mc")`, creating a reference schematic with `mcAddReference()`, inserting reference simulations into a target library with `mcShow()`, and handling common issues. The tool copies model files, generates a `savedc.scs` file, creates a Maestro view with default expressions and design variables, and supports gm/id-based simulations. Your may create your reference schematics for just once and reuse them multiple times in different projects.Your may create your reference schematics for just once and reuse them multiple times in different projects. 

## Start

Copy the two folders in this project to your **root working path** (the folder you place all your projects)

Run `load("mc")` to start the tool after starting virtuoso.

## Add a Reference Schematic

Run `mcAddReference()` to create a reference schematic. This shematic should include only one MOS device to scan the characteristics. Then click `Create blank schematic`. 

![alt text](https://moschar.elecannonic.com/README-asset/mcaddreference.png)

Draw your own reference device testing bench. For NMOS, we recommand utilizing the following structure. 

![alt text](https://moschar.elecannonic.com/README-asset/nmosref.png)

Make sure you have set the parameters properly: gate voltage `vin`, device size `L` and `W`. This tool will set the values automaticly. 

## Insert Reference Simulation to a Project

Run `mcShow()` to insert a reference to your project (library).

Select your target library and source reference. Existing references will be listed and you should select exactly one reference per time. Then name the cellview you aims to create. Then set your default parameter values: VDD, L and W. 

It will copy the model files from an existing library and create a `savedc.scs` file on the library path. So you are accessible to all DC parameters in scanning. 

![alt text](https://moschar.elecannonic.com/README-asset/mcshow.png)

If you want to add another reference (usually an NMOS and a PMOS), click Add another reference and repeat the steps above. When everything is done, click confirm. You will see your references have been added to your library. 

Meanwhile, a meastro will be automatically created based on your schematic and variables. Five commonly used fundamental expressions have been added by default. Your default variables are also pasted to the design variables. 


![alt text](https://moschar.elecannonic.com/README-asset/meastro.png)

Then you can run simulations based on your gm/id. 


## FAQ

- If an error reports that "This cellview is already registered. " but there are no cellviews with the same name in your target library, that means you have deleted them but virtuoso has not updated the memory yet. You should restart your virtuoso to resolve this problem.
- If you see a deleted cellview in the list after running `mcShow()`, the reason is the same as that above. Also restart virtuoso