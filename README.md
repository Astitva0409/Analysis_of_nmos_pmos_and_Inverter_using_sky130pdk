# Design_and_analysis_of_nmos_pmos_and_Inverter_using_sky130pdk

Welcome to the Design and Analysis project using the SkyWater130 Process Design Kit (PDK). In this project, we will explore the characteristics and behavior of NMOS and PMOS devices, as well as design and analyze a CMOS inverter, utilizing the capabilities of the SkyWater 130nm process technology.

**Analysis of NMOS and PMOS**

We will begin by utilizing the 1.8V standard models of NMOS and PMOS available in the SkyWater130 PDK. Through analysis and experimentation, we will explore the common working principles of these devices and characterize their behavior by varying different parameters. This analysis will provide valuable insights into their performance and functionality.

**Design and Analysis of CMOS Inverter**

Next, we will dive into the design and analysis of a CMOS inverter. This will involve creating the schematic representation of the inverter and measuring various parameters such as delay, noise margin, rise time, and fall time. These measurements will serve as a case study to study SPICE simulation and understand the behavior of the CMOS inverter.

**Layout Design using MAGIC**

In the subsequent phase, we will shift our focus to the layout design of the CMOS inverter using the MAGIC layout editor. MAGIC provides a comprehensive platform for exploring and utilizing the different layers available in the SkyWater130 PDK. We will create the layout design of the inverter, ensuring adherence to design rules and constraints.

**Layout versus Schematic (LVS) Comparison**

To ensure the accuracy and consistency of our layout, we will perform a Layout versus Schematic (LVS) comparison. This step involves comparing the layout design with the previously created schematic representation. By utilizing tools like Netgen and the LVS capabilities of the SkyWater130 PDK, we will verify the correctness and integrity of the layout.

Throughout the project, we will leverage the models and resources provided by the SkyWater130 PDK, as well as open-source tools such as Xschem, NGSPICE, MAGIC, and Netgen. The project documentation will be structured in a manner that is easily understandable for anyone looking to follow the same methodology.


# Content

 **1. About Tools**
 
1.1 Ngspice

1.2 Magic

1.3 Netgen

1.4 Xschem

1.5 Skywater Technology

 **2. Analysis of MOSFET models**

 2.1 General Mos Analysis

 2.2 Strong 0 and Weak 1

 2.3 Weak 0 and Strong 1
   

 **3. CMOS Inverter Design and Analysis**

 3.1 Why CMOS Circuits

 3.2 CMOS Inverter Analysis
 
  # 1. About Tools
  
   **1.1 Ngspice**
   


  [Ngspice](https://ngspice.sourceforge.io/) is an open-source mixed-level/mixed-signal electronic circuit simulator widely used for circuit design, analysis, and verification. It allows users to 
  model and simulate the behavior of electronic circuits using a variety of circuit elements, including resistors, capacitors, inductors, transistors, and more.

  Ngspice provides a command-line interface for interaction and scripting, making it flexible and suitable for both interactive usage and automated workflows. It 
  supports a wide range of circuit netlist formats, including the popular SPICE format, allowing seamless integration with existing design flows and tools.

   Its versatility and accessibility make it a valuable asset in the field of electronic design automation.

   > *You can refer to Ngspice manual [here](https://ngspice.sourceforge.io/docs.html)*

  <section id = "magic" nane = "magic" class = "anchor" >
   
  ## **1.2 Magic**

   [Magic](http://opencircuitdesign.com/magic/) is an open-source layout tool widely used in the field of digital integrated circuit design. It provides a powerful platform for creating and editing 
   layouts of integrated circuits at various levels of abstraction, ranging from individual transistors to complete chip designs.
   
   Magic offers a range of features to enhance productivity and design efficiency. It includes a comprehensive set of drawing tools and alignment aids to facilitate 
   precise and accurate layout creation. It supports design rule checking (DRC) and layout versus schematic (LVS) verification, helping to identify and resolve 
   potential design errors and mismatches.

   Its feature-rich nature, extensibility, and community support make it an invaluable asset in the realm of digital integrated circuit design.

   > *You can refer to Magic manual [here](http://opencircuitdesign.com/magic/magic_docs.html)*

</section>

   **1.3 Netgen**
   
 

   [Netgen](http://opencircuitdesign.com/netgen/) is an open-source netlist comparison and verification tool used in the field of electronic design automation (EDA). It provides a powerful platform for 
   analyzing and comparing digital circuit netlists to ensure consistency and correctness across different stages of the design process.

   Netgen supports a wide range of netlist formats, including popular industry standards like SPICE and Verilog. It offers comprehensive netlist parsing and analysis 
   capabilities, allowing you to explore the hierarchical structure of the design, examine signal dependencies, and identify potential issues.

   Its ability to detect discrepancies and ensure design consistency contributes to the overall success and reliability of your circuit designs.

   > *You can refer to Netgen manual [here](http://opencircuitdesign.com/netgen/tutorial/tutorial.html)*

   **1.4 Xschem**
   

   [Xschem](https://xschem.sourceforge.io/stefan/index.html) is an open-source electronic schematic capture and simulation tool widely used in the field of electronic design automation (EDA). It provides a versatile 
   platform for designing and simulating analog and digital circuits, facilitating the creation and analysis of complex circuit schematics.

   Xschem also supports advanced features such as model parameter extraction, sensitivity analysis, and waveform plotting, allowing you to fine-tune circuit designs 
   and explore design trade-offs. It offers a flexible scripting interface, enabling automation of repetitive tasks and customization of the tool's behavior to suit 
   specific requirements.

   Its user-friendly interface, extensive simulation capabilities, and community support make it an invaluable tool in the field of electronic design.

   > *You can refer to xschem manual [here](https://xschem.sourceforge.io/stefan/xschem_man/xschem_man.html)*

   **1.5 Skywater Technology**
   


   The [SkyWater](https://www.skywatertechnology.com/technology-and-design-enablement/) Technology Foundry 130nm Process Design Kit (PDK) is a comprehensive collection of files, libraries, and documentation that enables the design and 
   fabrication of integrated circuits (ICs) using the SkyWater 130nm process technology.

   The SkyWater130 PDK is typically utilized in conjunction with electronic design automation (EDA) tools, enabling designers to create and verify their IC designs 
   within a familiar design environment. The PDK provides the necessary information for layout design, including design rules, layer information, and guidelines for 
   ensuring compatibility with the SkyWater 130nm process technology.

   Overall, the SkyWater130 PDK is an essential resource for IC designers seeking to leverage the capabilities of the SkyWater 130nm process technology. Its 
   comprehensive set of files, libraries, and guidelines streamline the design process and facilitate the creation of high-quality integrated circuits.

   > *You can refer to skywater130 manual [here](https://skywater-pdk.readthedocs.io/en/main/)*

   ## Analysis of NMOS and PMOS

   *******************************
In this section, we will conduct an analysis of the NMOS and PMOS devices. For our analysis, we will utilize the basic 1.8V model available in the SkyWater130 PDK. While there are various other models available for different purposes, we will focus on this particular model for our analysis.

To begin, open the Xschem application. Upon startup, the application window will be displayed which will look like this.



Create a new schematic by selecting the ```File``` option and choosing to create a new file. A blank window will appear where we can build our schematic.


To instantiate the required components, use the shortcut ```Shift + I``` to open the component instantiation window. Here, you will find two libraries: "xschem device library" and "xschem_sky130 device library". Select the following components:

```nfet_01v8.sym``` from the xschem_sky130 library<br>
```vsource.sym``` from the xschem device library<br>
```code_shown.sym``` from the xschem device library<br>
```gnd.sym``` from the xschem device library<br>

```code_shown.sym``` block in Xschem is a versatile tool for adding custom code snippets, comments, or annotations within a schematic to convey additional information or highlight specific aspects of the design.

Connect the components using wires to create the desired schematic. Use the ```W``` shortcut to draw wires between the components. Your schematic should resemble the desired configuration.
