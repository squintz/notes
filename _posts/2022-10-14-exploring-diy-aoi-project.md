---
title: "Exploring: DIY AOI"
author: Squintz
categories: [Exploring]
tags: [Exploring, AOI, OpenCV, Python, C#]
math: true
mermaid: true
---

## Project Overview

I'm an electronic technician and my son is in college working on his electrical engineering degree. As a proud father I want to work on projects together with him. So we're working on teaching ourselves about techniques used to inspect assembled circuit boards. Thus our DIY Automatic Optical Inspection (AOI) project is born. This page will contain random notes. Don't expect anything cohesive or well thought out here!

## Our Plan

* [ ] Autodetect the boards position and contours to scale the image relative to the known PCB size.
* [ ] Read the Pick and Place (PNP) files to obtain approximate locations of components.
* [ ] Read Gerbers to extract exact pad dimensions and locations
* [ ] Use YOLO to identify component defects
* [ ] Build or purchase an XYZA table or delta bot if necessary to get images from various angles.

## OpenCV Contour Sorting

Contour detection and sorting is useful for drawing bounding boxes around things. However, it seems like it's not very practical using cheap USB microscope cameras.

Resources:

* [https://cvexplained.wordpress.com/tag/contours/](https://cvexplained.wordpress.com/tag/contours/)
* [https://stackoverflow.com/questions/69074165/order-of-corners-in-a-rotating-rectangle-in-opencv-python](https://stackoverflow.com/questions/69074165/order-of-corners-in-a-rotating-rectangle-in-opencv-python)
* [https://imaginghub.com/projects/221-automatic-optical-inspection-of-printed-circuit-boards](https://https://imaginghub.com/projects/221-automatic-optical-inspection-of-printed-circuit-boards)
* [https://www.bobbaddeley.com/2015/12/06/creating-an-automated-optical-inspector-for-50/](https://www.bobbaddeley.com/2015/12/06/creating-an-automated-optical-inspector-for-50/)

## PCB Files

Since this AOI is intended to be use by the developer of the PCBs there is no concern over using the PCB files as input to make our job easier. We have access to:

* Schematics and Layout source files
* Gerbers, BOMs, and PNP

### Gerbers

Gerber RS-274X Specification: https://d1.amobbs.com/bbs_upload782111/files_11/ourdev_450330.pdf

* Doesn't contain reference designators
* Python Libraries exist to import the files.
* Could be used to extract exact pad sizes. May be useful in conjunction with PNP and BOMs to identify component designators, footprints, and individual pads.
* We may be able to use this to read the gerber files and extract pad information. [https://github.com/curtacircuitos/pcb-tools/blob/master/gerber/rs274x.py](https://github.com/curtacircuitos/pcb-tools/blob/master/gerber/rs274x.py)

### BOMs

* Not very useful as PNP has the same information

### Pick and Place (PNP)

* Contains: RefDes, Name, Pattern, CenterX, CenterY, Side, Rotate, Value, Package Height, OriginX, OriginY, FirstPadX, FirstPadY
* Does not contain pad or package dimensions.

