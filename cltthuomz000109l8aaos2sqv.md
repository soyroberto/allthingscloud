---
title: "Explain further The Manhattan distance from cell C to cell I is 2 (moving 1 unit horizontally and 1 unit vertically)."
datePublished: Sat Mar 16 2024 02:53:57 GMT+0000 (Coordinated Universal Time)
cuid: cltthuomz000109l8aaos2sqv
slug: explain-further-the-manhattan-distance-from-cell-c-to-cell-i-is-2-moving-1-unit-horizontally-and-1-unit-vertically
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1710557579847/8c6f52a3-4ba4-4de6-9e3f-dfce41c337e0.jpeg
tags: ai, chatgpt

---

Certainly! In a grid-based pathfinding problem like the one described, the Manhattan distance is calculated by summing the absolute differences in the x and y coordinates of two points.

Let's take a closer look at the grid and the positions of cell C and cell I:

```excel
   A (1, 1)    B (2, 1)    C (3, 1)
   D (1, 2)    E (2, 2)    F (3, 2)
   G (1, 3)    H (2, 3)    I (3, 3)
```

**<mark>The x-coordinate represents the horizontal position of a cell, and the y-coordinate represents the vertical position</mark>**. Each cell in the grid has a unique (x, y) coordinate pair.

In this example:

* Cell C has coordinates (3, 1), because it's in the third column (x-coordinate) and the first row (y-coordinate).
    
* Cell I has coordinates (3, 3), because it's in the third column (x-coordinate) and the third row (y-coordinate).
    

To calculate the Manhattan distance between cell C and cell I:

1. Compute the absolute difference between their x-coordinates: |3 - 3| = 0.
    
2. Compute the absolute difference between their y-coordinates: |1 - 3| = 2.
    

Finally, sum the absolute differences: Manhattan distance = 0 (horizontal distance) + 2 (vertical distance) = 2.

So, the Manhattan distance from cell C to cell I is 2. This means that it would take two moves to reach cell I from cell C, moving 1 unit horizontally and 1 unit vertically.

Sure! Here's the updated grid with the coordinates added:

Now, each cell in the grid is labeled with its corresponding coordinates in the format (x, y), where:

* x represents the horizontal position (column number).
    
* y represents the vertical position (row number).
    

With these coordinates, it's easier to identify the positions of the cells and compute distances between them.