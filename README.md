# MEC1003F 2024 Assignment 3

Starting repository for MEC1003F 2024 Assignment 3.

## Overview

For this assignment you will demonstrate your ability to layout and route a PCB. You are given a schematic with some components and all footprints completed, and you will need to complete the PCB from here.

Bonus marks are also available for exporting the design to Gerber files. Note this was not yet covered fully in lectures, but this will be required for the class test so best to get some practice and bonus marks in now.

In the last assignment the schematic was for a basic relaxation oscillator and level shifter, and you added a voltage regulator to provide a 3.3V supply. Now in this schematic there is additionally 2 dual D Flip-Flops which divide the frequency of the oscillator by 16. This is a proper circuit! It will take you some time to practice laying out various arrangements before you get a good one, and so this assignment will take a little longer than the last two. Beware and start on it early!

## Initial Instructions

1. Clone or download this repository to your local machine. If downloading manually, remember to extract the contents of the .zip file!
2. Open the KiCad project by opening the `.kicad_pro` file. This will open the project in KiCad.
3. Open the schematic in KiCad. You should notice the following changes:
    - All components have had their footprints created by yours truly. Cross check the TO-252 footprint to check your work from Assignment 2.
    - New circuitry for 2x Dual D Flip-Flops has been added. This configuration is detailed a little in the datasheet - try figure out what it does!

> [!TIP]
> The symbol for the Dual D Flip Flops are multi-unit symbols. This means each whole component has been broken down into multiple parts, which has benefits for a part like this. The designators gain an alpha suffix (e.g. U1A, U1B, U1C, etc.). The pins across all parts sum to the whole component. Check out the symbol to see how this is made!

3. **Edit the schematic page info to enter your student name and number!!!**
4. Open the PCB Editor. You should find this blank. Update the PCB with the schematic info and place all the components. Take a look in the 3D viewer and see what's happening!

> [!NOTE]
> Sometimes the project footprints library won't load if opening in a different KiCad version. If you have issues with the footprints, you can add the library manually. Go to `Preferences > Manage Footprint Libraries > Project Specific Libraries > Add Existing` and add the `Project Footprints` library from the project folder directory.

With this you should have the general outline of the project you are working with.

## Tasks

### 1. Set the Design Rules (5 marks)

Before you start laying out the PCB, you should set the design rules. This is important to ensure that the PCB is manufacturable.

- Open the PCB Editor and go to `File > Board Setup > Design Rules > Constraints`.
- Set all relevant basic design rules according to the capabilities of JLCPCB (https://jlcpcb.com/capabilities/pcb-capabilities).

> [!TIP]
> Setting some appropriate pre-defined sizes for tracks and vias now can also help ensure you conform to the design rules.

The tutors are skilled that they can easily tell from the PCB if you set a bad design rule or not. Remember to consider the PCB manufacturing process, and consider the components you are using, and set appropriate margins for the design rules.

It is absolutely not required to program custom rules, but if you want to, you can and these can be helpful.

### 2. Layout Components (5 marks)

Reorientate all components to a layout that makes sense. There are a lot of components now, so remember the method shown in lecture that can help simplify the process:

- Open the PCB and Schematic editors side by side and ensure cross-probing is enabled. Use this to keep track of what's what.

> [!TIP]
> If cross probing is not working, check `Preferences > Schematic Editor > Display Options > Cross Probing` and ensure it is enabled.

- Hide the Silkscreen and other unnecessary layers for now. You can do this by clicking the eye icon in the right UI column. We can deal with the non-critical layers later.
- Identify the various groups of components (e.g. oscillator, level shifter, voltage regulator, flip-flops) with the supporting peripheral components. Separate these groups of components in the PCB editor.
- For each group now move, rotate and layout the components in a way that makes general sense and as best you can understand the function of each component within these groups.

> [!TIP]
> Setting an appropriate grid size can help with this (topmost icon in the left UI column). Try a grid size of 0.5mm.

- Don't route yet! Try use the ratsnest lines to tell if the layout is ok. Ignore the big nets for power and ground for now, or you can hide these lines by right clicking on the net name on a pad and selecting `Net Inspection Tools > Hide net in Ratsnest`.

### 3. Route (5 marks)

Now that you have a basic layout that makes sense, you can start routing these groups.

- To start, just route the short nets local to the groups you've laid out. Remember the shortcut 'X' to start routing. Ignore the input, output, power and ground nets between components (although obviously still consider how these will come in and out later).
- Ensure you use an appropriate track width and via size, and toggle through your preferred sizes with 'W'. At a minimum, you must have different track widths for power and signal lines.
- Simply route `GND` nets to a quick via and drop them to the bottom layer. We will place a ground pour on the bottom layer later which will connect all the GND vias. Similarly, we will route in `+BATT` and `+3V3` later.
- You cannot possibly complete the routing without the use of some vias. Use them! Shortcut 'V'. Just remember to keep routing on the bottom layer short and sweet - we want to reserve that layer for `GND` as much as possible.

### 3. Board Outline, Final Layout, and Ground Pour (4 marks)

- Draw a board outline (on the Edge.Cuts layer) for this PCB, set it as a 50x50mm square. Remember this is the typical smallest handling size for JLCPCB without added costs.
- Place a ground pour on the entire bottom layer. This will connect all the GND vias you've placed. Remember to set the net to `GND` in the properties of the pour.
- Place the crocodile bite pads as connectors around the board edge.
- Now, move the semi-routed groups of components to a final layout that makes sense relative to one another. There's no prize for using less than the full 50x50mm, so keep this simple and logical in location and rotation.
- Complete the routing of the remaining inter-group nets and the power and ground nets. Reflow the ground pour if necessary with 'B'.

### 4. Final Details (2 marks)

Now unhide the silkscreen and other hidden layers. Place these elements appropriately and ensure the designators ad other drawing elements are visible and not overlapping, and indicate the designation of each and every component.

> [!TIP]
> Dimming other layers ('H') can help focus and setting the active layer helps preference selecting items on that layer.

For this assignment you **must** place all silkscreen designators.

Finally, add your name, student number, version, and any other details you want to the silkscreen. This is a good habit to get into for your own projects. You are also welcome to add things like mounting holes, etc if you really want the prize for top design!

### 5. Checks

Before you submit, check your design thoroughly for errors. Especially, this means run the Design Rule Check (DRC) and ensure there are no errors. The tutors are skilled enough to see most errors by eye, and to know what errors are critical vs what can be waived. Go through each error and either resolve it or, if you are confident the error or warning is not actually an issue, dismiss it. So if you choose to dismiss a DRC error, make 100% sure you are justified in doing so given your understanding of the manufacturing process.

**Before you submit, there should be zer DRC errors and preferably no warnings.**

Simply viewing the PCB in 3D view can also help you spot any obvious issues in component placement.

### 6. Bonus: Gerber & Drill Export (+2 marks)

Export the PCB to Gerber and Drill files. This is not required for the assignment (bonus marks), but it is good practice and will be required for the class test. You can do this by going to `File > Fabrication Outputs > Gerber Files` and following the prompts. Also remember to export the Drill files too. Follow the instructions by JLCPCB for this (https://jlcpcb.com/help/article/362-how-to-generate-gerber-and-drill-files-in-kicad-7), and set the output folder to "Fabrication" in the project directory.

You can then view the Gerber files in a Gerber viewer to check the design, or better upload a .zip of the fabrication output to JLCPCB!

## Submission Instructions

ZIP the entire project folder and submit it to Amathuba. Remember to include your student number in the schematic page info and PCB silkscreen!

## Support

Remember that you can ask for help at any time. Post your questions on MS Teams Under the `Assignments` channel or otherwise contact the lecturer for some hints. This is an important assignment and we want you to do well and get comfortable doing this!
