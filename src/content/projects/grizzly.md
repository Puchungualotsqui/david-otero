---
title: Grizzly DataFrame
description: >-
  Grizzly is a DataFrame library for Go, designed to harness the full power of GoRoutines for handling large datasets efficiently. Its core aim is to provide an easy-to-use, yet robust, solution for data manipulation while maximizing the computational capabilities of modern machines through parallelized task execution.
image: '@assets/projects/grizzly/image.png'
startDate: 2024-05-27
endDate: 2024-08-10
skills:
  - Go
  - Multithreading
  - No dependencies
sourceLink: https://github.com/Puchungualotsqui/GrizzlyDataFrame
featured: true
---
### Features
- Typed DataFrame (float64 and string)
- Data aggregation and statistical functions
- Data attributes and metadata handling
- Import and export utilities
  
### Installation
To install the package, use:
```
go get github.com/Puchungualotsqui/grizzly
```
If you have problems. Please, try to download directly the package.
## Basic Usage
### Creating a DataFrame

```
package main

import (
	"fmt"
	"grizzly"
)

func main() {
	names := []string{"Alice", "Bob", "Charlie", "Diana", "Ethan"}
	ages := []float64{25, 30, 35, 40, 28}

	// Initialize the DataFrame
	df := grizzly.CreateDataFrame()

	// Add columns
	df.CreateStringColumn("Names", names)
	df.CreateFloatColumn("Ages", ages)

	df.PrintHead(5)
}
```
