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

##### ST7735_XYplotInit
This function fills the screen black using `ST7735_FillScreen`, sets the background color for the plot using `ST7735_FillRect`, outputs the title, and sets the endpoints min and max values of the plot.

\
##### ST7735_XYplot
This function plots the values in the buffer using `ST7735_DrawPixel`. The plot coordinates are caluclated using the following lines of code

```
			plot_x = (127 * (cur_x - min_x))/(max_x - min_x);
			plot_y = 32 + (127 * (max_y - cur_y))/(max_y - min_y);
```

## Measurement Data

No measurement data for this lab

## Analysis and Discussion

*When should you use fixed-point over floating point? When should you use floating-point over fixed-point?*

	[Insert answer here]

*Give an example application (not mentioned in the book) for fixed-point. Describe the problem, and choose an appropriate fixed-point format. (no software implementation required).*

	[Insert answer here]

*Can we use floating point on the ARM Cortex M4? If so, what is the cost?*

	[Insert answer here]

*OPTIONAL: When should you use binary fixed-point over decimal fixed-point? When should you use decimal fixed-point over binary fixed-point?*

	[Insert answer here]

