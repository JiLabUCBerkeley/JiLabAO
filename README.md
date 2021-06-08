# JiLabAO
Standalone application for aberration measurement and correction. 

Details of the AO method and applications to two-photon and three-photon fluorescence microscopy can be found at: https://www.biorxiv.org/content/10.1101/2020.11.25.397968v1

![3P_AO_Cortex-01](https://user-images.githubusercontent.com/82175337/121226122-0eb26800-c83f-11eb-8368-7d51a25e666a.png)

# I. Introduction
This is a standalone control software for an adaptive optics (AO) module developed in the JiLab for aberration measurement and correction. It was designed to work with a hexagonal tip-tilt-piston deformable mirror (DM) manufactured by Boston Micromachines Corporation (Hex-111-X). Below we describe how to install and run this application. You can test it by running it in simulation mode, without the need of having the DM or a data acquisition (DAQ) device connected to your computer (check out the video *JiLabAO_Getting_Started*, demonstrating how to run this control software in simulation mode).

# II. Getting started #1 (not testing on a microscope yet)
If you would like to see how this module works, you can test it without having a DM or DAQ already by following the steps below:

### Making a local copy of all files
Please download all files from the repository locally into your computer.

### Installation
This standalone control software was written in LabVIEW. To run it in your computer, you will first need to run the installer: *standalone.exe*, located at *JiLabAO/Standalone AO Installer/Volume/*. This will install the LabVIEW Runtime Engine and all the files the software needs in order to run.

# III. Running the application in simulation mode

### Open *JiLabAOModule.exe*
If you have not installed the PCIe card (designed to interface with the X-CL 140 driver) and corresponding driver, you will see the following error message when you open *JiLabAOModule.exe*: “An error occurred in program. Do you wish to continue?”. Please click “Return to Idle”.

### Turn on simulation mode
On the bottom right corner of the main interface, please turn on the control called “Simulation mode”. When this option is selected, the software will use PMT data obtained experimentally and load it into the program – rather than acquiring the PMT data using real hardware. This data is located in the folder *JiLabAO/SimulationFilesStandAlone/*.

### Run AO routine
Please refer to the video *JiLabAO_Getting_Started*, which demonstrates how to run the AO routine. Make sure the parameters on the “Adaptive Optics” and “System Configuration” tabs are set to the values shown on the screenshots below.

Adaptive Optics settings             |  System Configuration settings
:-------------------------:|:-------------------------:
![AdaptiveOpticsSettings_small](https://user-images.githubusercontent.com/82175337/121077302-53c99200-c78c-11eb-872e-b3563411bf16.PNG) |  ![SystemConfigurationSettings_small](https://user-images.githubusercontent.com/82175337/121077318-57f5af80-c78c-11eb-81fc-660997006724.PNG)

                                                                                                                                         
# IV. Getting started #2 (ready to use on a microscope)
If you have the DM and DAQ and are ready to use this module on a microscope, please follow the steps below (you must have succesfully completed the previous steps).

### Install PCIe card and driver
Please refer to the DM manufacturer’s user manual for installation details.

### Connect DAQ
Connect the DAQ device into your computer and make sure its corresponding driver is installed. Then, go to “Hardware Acquisition In>Channel” in the “System Configuration” tab of the main interface. Your DAQ device should now appear in the list of devices.

Note: We tested this software control program using the DAQ device USB-6361 from National Instruments, offering a maximum sample rate of 2 Ms/s.

### Generate bin files
The bin files are unique to each DM. You will need the lookup table provided by BMC to generate such files, and place them in the *JiLabAO/bin files/* folder.

# IV. Running the application on your microscope. 
Once you succesfully complete all the steps described above, and you have properly integrated and aligned the AO module (DM, conjugating lenses, and filed stop) into your microscope, you are ready to go!

- Enter the desired settings on the “Adaptive Optics” and “System Configuration” tabs. 
- Using the imaging software that controls your microscope, find a fluorescent feature to run the AO routine on. 
- Park the laser in this location, open the mechanical shutter of your microscope, and run the AO routine.
- Once the AO routine completes, close the mechanical shutter.
