Section 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK 
Theory
Expand or Collapse
Implementation
Section 1 tasks:-

Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
Calculate the flop ratio.
Flop Ratio = No.of D Flipflops/Total Number of Cells
Percentage of DFF's = FlopRatio*100

1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
Commands to invoke the OpenLANE flow and perform synthesis

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# Start docker
docker
```
```bash
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

# Exit from OpenLANE flow
exit

# Exit from OpenLANE flow docker sub-system
exit
```

'''
![Alt Text](openlane_interactive.png)

![Alt Text](Synthesis_succesful.png)
![Alt Text](after_synthesis.png)

   Flop Ratio = 1613/14876 = 0.10842968539
 
   = 0.10842968539*100 = 10.842968539

![Alt Text](in_report_dff_ratio.png)
# Digital VLSI SoC Design and Planning <br>
This repository documents my hands-on learning of ASIC Physical Design using the OpenLANE flow.<br>
It covers the complete RTL-to-GDSII flow through structured day-wise implementation.

![main picture](https://github.com/user-attachments/assets/d5db9f8d-21fa-44cd-ab4e-d7706c8ca6bf)

## Objectives:

 -Understand complete ASIC Design Flow <br>
-Gain practical exposure to OpenLANE <br>
-Analyze synthesis, floorplanning, placement, and routing <br>
-Perform timing and design analysis <br>

## Tools & Technologies:
-OpenLANE <br>
-Sky130 PDK <br>
-Docker <br>
-Magic VLSI <br>

## Branches:
->Main Branch <br>
-> Day-1 <br>
-> Day-2 <br>
-> Day-3 
