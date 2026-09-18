# Image Transformation Toolbox

**Course:** System Modelling, Analysis and Stories - 1 (SMAS-1)  
**Assignment:** Assignment 3 - Linear Transformations  
**Questions covered:** Q10 and Q11

## Overview

This Google Colab notebook demonstrates how geometric transformations can be applied to a JPG or PNG image. An uploaded image is treated as a collection of pixel locations, and the toolbox provides an interactive menu for applying common transformations.

The project connects the visual effects of image editing with the linear-algebra ideas used in the assignment: matrices, transformations of coordinate vectors, rank, and information loss.

## Features

After uploading an image, choose an operation from the menu:

| Menu option | Description |
| --- | --- |
| Rotate | Rotates the current image by a user-entered angle. |
| Resize | Scales the width and height by a user-entered factor. |
| Flip | Mirrors the image horizontally or vertically. |
| Shear | Applies a horizontal shear using a user-entered shear value. |
| Custom Matrix | Accepts a 2 x 2 matrix and applies it as an affine transformation. |
| Reset | Restores the originally uploaded image. |
| Exit | Ends the program. |

The image is displayed after every operation, so the effect of each transformation can be observed immediately.

## Running the Notebook in Google Colab

1. Open the notebook in [Google Colab](https://colab.research.google.com/).
2. Paste the program into a code cell and run it.
3. Upload a JPG or PNG image when the upload dialog appears.
4. Enter a menu number in the output area.
5. Provide the requested value, such as an angle, resize factor, shear value, or matrix entries.
6. Use `6` to reset the image at any time and `7` to exit.

## Libraries Used

The notebook uses the following Python libraries:

```python
from google.colab import files
from PIL import Image, ImageOps
import matplotlib.pyplot as plt
import numpy as np
```

Google Colab already includes these libraries in most sessions. If the code is run outside Colab, remove or replace `files.upload()` with a local image-file path.

## Linear-Transformation Connection (Q10)

The assignment asks for the following matrices to be interpreted and visualised. They can be entered through **Custom Matrix** (when applicable), while the other menu operations also provide practical visual examples.

| Matrix | Transformation | Rank | Information lost? |
| --- | --- | ---: | --- |
| $A_1 = \begin{bmatrix}2&0\\0&0.5\end{bmatrix}$ | Horizontal stretch and vertical compression | 2 | No |
| $A_2 = \begin{bmatrix}0&-1\\1&0\end{bmatrix}$ | 90 degree counter-clockwise rotation | 2 | No |
| $A_3 = \begin{bmatrix}1&1\\0&1\end{bmatrix}$ | Horizontal shear | 2 | No |
| $A_4 = \begin{bmatrix}-1&0\\0&1\end{bmatrix}$ | Reflection in the y-axis | 2 | No |
| $A_5 = \begin{bmatrix}1&0\\0&0\end{bmatrix}$ | Projection onto the x-axis | 1 | Yes; vertical-position information is lost |

For a matrix $A$, its columns are the images of the standard basis vectors: $T(e_1)$ is the first column and $T(e_2)$ is the second column. This is why the columns determine the geometric effect of the transformation.

### Basis-vector images for Q10

| Matrix | $T(e_1)$ | $T(e_2)$ |
| --- | --- | --- |
| $A_1$ | $(2,0)$ | $(0,0.5)$ |
| $A_2$ | $(0,1)$ | $(-1,0)$ |
| $A_3$ | $(1,0)$ | $(1,1)$ |
| $A_4$ | $(-1,0)$ | $(0,1)$ |
| $A_5$ | $(1,0)$ | $(0,0)$ |

## Files for Submission

Keep the following items together in the GitHub repository folder:

```text
image-transformation-toolbox/
|-- README.md
|-- image_transformation_toolbox.ipynb
`-- sample-image.jpg
```

Replace `sample-image.jpg` with the actual JPG or PNG used while testing the notebook.

## Notes

- Transformations are cumulative: each operation changes the current image.
- **Reset** returns to the first uploaded image.
- Use a positive resize factor greater than zero.
- The custom-matrix option accepts entries in row order: `a`, `b`, `c`, `d`, representing $\begin{bmatrix}a&b\\c&d\end{bmatrix}$.

