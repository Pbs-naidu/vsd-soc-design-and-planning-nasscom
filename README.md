
Section 2 – Comparison of Efficient and Inefficient Floorplans & Overview of Standard Cell Libraries (16/03/2024 – 17/03/2024)
Conceptual Understanding
Study the characteristics that distinguish a well-optimized floorplan from a poorly structured one.
Gain a basic understanding of standard cell libraries and their role in VLSI design.
Practical Implementation
Execute design steps using the OpenLANE flow and analyze the outputs at different stages.
Section 2 – Assigned Tasks
Perform the floorplanning stage for the picorv32a design using the OpenLANE flow and generate the corresponding output files.
Extract the dimensions from the generated floorplan DEF file and compute the total die area in micrometers.
Import the floorplan DEF file into the Magic layout tool and examine the overall floorplan structure.
Execute congestion-aware placement for the picorv32a design using OpenLANE and obtain the resulting outputs.
Load the placement DEF file into Magic and analyze the placement distribution and cell arrangement.
Running Floorplanning in OpenLANE

Use the OpenLANE flow commands to initiate and complete the floorplanning stage for the design, ensuring all required outputs are successfully generated.
```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```


```bash
# Now we can run floorplan
run_floorplan
```
Screenshot of floorplan run
![Alt Text](floorplan.png)

2) Load generated floorplan def in magic tool and explore the floorplan.
Commands to load floorplan def in magic in another terminal
```bash
# Change directory to path containing generated floorplan def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/17-03_12-06/results/floorplan/

# Command to load the floorplan def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
![Alt Text](floor_plan.png)

Equidistant ports

![](floorplan_select..png)

Port layer 

![](floorplan_select.png)

![](floorplan_standard_cell.png)


