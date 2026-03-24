Section 3 - Design library cell using Magic Layout and ngspice characterization (18/03/2024 - 21/03/2024)
Theory
Implementation
Section 3 tasks:-
Clone custom inverter standard cell design from github repository: Standard cell design and characterization using OpenLANE flow.
Load the custom inverter layout in magic and explore.
Spice extraction of inverter in magic.
Editing the spice model file for analysis through simulation.
Post-layout ngspice simulations.
Find problem in the DRC section of the old magic tech file for the skywater process and fix them.
```bash
1. Clone custom inverter standard cell design from github repository
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Clone the repository with custom inverter design
git clone https://github.com/nickson-jose/vsdstdcelldesign
```
![Alt Text](after_git_clone_and_copying_sky130A_to_vsdstdcell.png)

```bash
# Change into repository directory
cd vsdstdcelldesign

# Copy magic tech file to the repo directory for easy access
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .

# Check contents whether everything is present
ls

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &
```
2) Load the custom inverter layout in magic and explore.
custom inverter layout in magic
![Alt Text](layout.png)
![Alt Text](polysilicon_layout_pmos.png)
![Alt Text](double_s_click_gnd.png)
![Alt Text](double_s_click_power.png)

3) Spice extraction of inverter in magic.
Commands for spice extraction of the custom inverter layout to be used in tkcon window of magic
```bash
# Check current directory
pwd

# Extraction command to extract to .ext format
extract all

# Before converting ext to spice this command enable the parasitic extraction also
ext2spice cthresh 0 rthresh 0

# Converting to ext to spice
ext2spice
```
 tkcon window after running above commands
 ![Alt Text](extract_all.png)
![Alt Text](ext_to_spice_command.png)
Screenshot of created spice file
 ![Alt Text](inspice_file.png)

4) Editing the spice model file for analysis through simulation.
Measuring unit distance in layout grid
  ![Alt Text](box_dimension.png)

edited spice file ready for ngspice simulation

  ![Alt Text](allpolynonres_in_uhrpoly_sec.png)
   ![Alt Text](vim_spice_command_update_3.png)
   
5) Post-layout ngspice simulations.
 
Commands for ngspice simulation
```bash
# Command to directly load spice file for simulation to ngspice
ngspice sky130_inv.spice

# Now that we have entered ngspice with the simulation spice file loaded we just have to load the plot
plot y vs time a
```

Screenshots of ngspice run
 ![Alt Text](ngspice.png)
 ![Alt Text](plot_y_vs_time.png)
 
 Rise Transition Time=t80%​−t20%​
 20% of Output Voltage = 0.2×Vout​=0.66 V
 80% of Output Voltage = 0.8×Vout​=2.64 V
 Rise Time=t(2.64V)−t(0.66V)

 Rise:
 20% 
 
 ![Alt Text](20_and_80_percent_rise_cmd_coordinates.png)
![Alt Text](20_percent_rise_waveform).
Rise Transition Time = 5.5193 - 5.1866 = 0.3327 ns

Fall:
80%
  ![Alt Text](80_to_20_fall_cmd_cordinates.png)
![Alt Text](20_percent_fall_waveform).

Fall Transition Time = 5.70097 - 4.50096 = 1.20001 ns

50%
 ![Alt Text](rise_and_fall_50_percent_rise_delay_cmd.png)
![Alt Text](rise_and_fall_50_percent_rise_delay_waveform).
