# EE 445L Lab 1 Report

Arjun Ramesh (ar59872)

## Objectives

* This lab focused on how to write graphic driver functions for the ST7735 LCD. To complete this lab, we had to implement two functions: `ST7735_XY_PlotInit` and `ST7735_XYplot` that initialize a plot on the screen and plot points respectively.
* The topics covered in the lab included LCD pixel plotting on the ST7735 and hardware interfacing of the LCD. 
* The purpose of this lab was to learn how to interface the LCD and write basic software modules that augment an existing library. 

## Hardware Design

No hardware design for this lab

## Software Design

### Plot.h
This file contains the function definitions of the two methods: `ST7735_XY_PlotInit` and `ST7735_XYplot`.

### Plot.c 

This file contains the implementations of the two functions from it's respective .h file.<br><br>

#### ST7735_XYplotInit
This function fills the screen black using `ST7735_FillScreen`, sets the background color for the plot using `ST7735_FillRect`, outputs the title, and sets the endpoints min and max values of the plot.


#### ST7735_XYplot
This function plots the values in the buffer using `ST7735_DrawPixel`. The plot coordinates are caluclated using the following lines of code

```
	plot_x = (127 * (cur_x - min_x))/(max_x - min_x);
	plot_y = 32 + (127 * (max_y - cur_y))/(max_y - min_y);
```

## Measurement Data

No measurement data for this lab

## Analysis and Discussion

*When should you use fixed-point over floating point? When should you use floating-point over fixed-point?*

	Floating point should be used over fixed-point when you want to represent very small or very large numbers. In this case, inaccuracies are acceptable for large numbers.  Fixed point is not well suited to that since it would require too many bits. However, fixed-point has a constant resolution unlike floating point, so it makes it more convenient and faster for applications that use numbers that are within certain limited bounded regions.

*Give an example application (not mentioned in the book) for fixed-point. Describe the problem, and choose an appropriate fixed-point format. (no software implementation required).*

	Assume a real-time digital signal processing application that takes in input between 0 and 5V and performs some transformation processes with minimal amplification (<4). Assume we have 32-bit representations. In this case, fixed-point makes more sense than floating point since the range of input voltages is small. We can represent values almost as accurately with floating point, but it is more power intensive and takes too much time to compute. This is an issue for real-time systems that need to guarentee delivered data within a certain time frame.
    A 32-bit fixed point format with 6 bits for the integer part and 26 bits for the fraction would be very accurate and execute much faster than it's floating point equivalent and help the system meet its criteria.

*Can we use floating point on the ARM Cortex M4? If so, what is the cost?*

    Yes, we can use floating point on the Cortex M4. It needs to be enabled separately, and requires a separate functional unit to compute floating point expression. This is also much slower than fixed point arithmetic and more complex in circuit design.


