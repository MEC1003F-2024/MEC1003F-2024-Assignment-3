# MEC1003F Lecture 2 Demo

KiCad Demonstration Project for UCT MEC1003F 2024

## Lesson Plan

In this lecture you will use this demo project to learn how to create footprints, layout a PCB, and route traces and vias to make some basic connections between components.

## Overview

Open the KiCad project file [MEC1003F-2024-Lecture-2-Demo.kicad_pro](MEC1003F-2024-Lecture-2-Demo.kicad_pro) in KiCad and check out the schematic. You should recognise a familiar AP331A comparator with some passive components! Again, this is not about the circuit design, but for those curious the first comparator circuit is a simple relaxation oscillator, while the second is simple hysteresis comparator which translates the output to another voltage level.

The operation of the circuit isn't that important, for us it is simply two IC components with a bunch of passives we can use as practice for layout and routing.

Although the schematic looks complete, the components aren't quite ready for layout. And so we begin!

## PCB Information

Before we can dive right into it we must first learn a bit more about PCBs and how they are modelled in EDA tools like KiCad. Pay attention in lecture as we explain the following key things:

- **Layer Stackup**: The PCB is made up of multiple layers, each with a specific purpose. Each of these layers is modelled as either 2D layers or other properties of the PCB file.
- **Technical vs User Layers**: Some layers in KiCad are simply for human reference, while others are used for specific purposes like copper, the board outline, solder mask, and silkscreen.
- **Courtyards and Spacing**: Components cannot be placed too close together, and so we most often draw a courtyard around the component to show the minimum spacing required.

## Footprints

### Task 1: Crocodile Pad

Most circuits need a way to connect to the outside world. This is usually done with a connector, but for this demo we will use a simple crocodile clip pad. This is a simple through-hole pad with copper on each side which can be used to bite down onto with a crocodile clip.

In the lecture we will explain how to create a new footprint for this pad and then update the symbol.

### Task 2: Comparator

Like the crocodile pad, the comparator footprint is not assigned. However, this is a bit more complicated as the footprint is a SOT-23-5 which is specified in the datasheet.

In the lecture we will demonstrate how we might go about creating a new footprint per the specification.

### Task 3: Passive Components

Some of the passive components are also not assigned. Although we could create new footprints for these.. these are just simple chip components. Assuming they are close enough, we will instead use the existing footprints from the KiCad standard library to save some time.

## PCB & Layout

Once we have all the footprints assigned, we can start the PCB layout. This is where we will place the components and route the traces to make the connections.

Follow the instructions in lecture to update the PCB with the schematic components, and then place and route the components.

This is a very hard task to explain in words, and practise is the only way to get the grip of layout & routing, but with some tips and tricks you should be able to get a good start.

### Key PCB Elements

While routing the PCB, pay attention to learn how to place the following key elements:

- **Board Outline**: The outline of the PCB is important to define the shape of the board. This is usually drawn on the Edge.Cuts layer.
- **Traces**: The most important part of the PCB is the copper traces which connect the components. These are drawn on the Copper layers.
- **Vias**: To connect traces on different layers, we use vias. These are plated holes which connect the copper on different layers.
- **Copper Pours**: Sometimes we need to fill an area with copper, either to provide a ground plane, make a heatsink, or just to make a non-uniform trace. This is done with a copper pour or "filled zone".

## Next Lecture

In this lecture we were just focusing on getting things onto the PCB and how to route them. In the next lecture we will focus on the design rules and how to check that the PCB is manufacturable. We'll also go a step further and consider some of the specific requirements for JLCPCB, the PCB manufacturer we will be using most often.
