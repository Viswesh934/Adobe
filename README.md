# Curve Regularization and Symmetry Detection

## Overview

This project focuses on the regularization and symmetry detection of 2D curves represented as polylines. The primary goal is to process these polylines and output regularized, symmetric curves in the form of cubic Bezier curves.

## Problem Statement

The input polylines for curve regularization and symmetry detection are classified into the following categories:

### 1. Isolated Curves
- **Description**: Simple input curves where each shape is a single polyline. The task is to regularize these isolated curves to maintain or enhance their geometric properties.
- **Examples**:
  - Input: `examples/isolated.csv`
  - Expected Output: `examples/isolated_sol.csv`

### 2. Fragmented Shapes
- **Description**: Shapes built from a collection of polylines. The challenge is to identify regular shapes and symmetry within a subset of these polylines.
- **Examples**:
  - Input: `examples/frag0.csv`, `examples/frag1.csv`
  - Expected Output: `examples/frag01_sol.csv`
  - Input: `examples/frag2.csv`
  - Expected Output: `examples/frag2_sol.csv`

### 3. Connected Occlusion
- **Description**: The occluding shape partially blocks the occluded shape, but the shape remains connected and can be represented by a single polyline.
- **Examples**:
  - Input: `examples/occlusion1.csv`
  - Expected Output: `examples/occlusion1_sol.csv`

### 4. Disconnected Occlusion
- **Description**: The occluding shape fragments the occluded shape into multiple closed paths (polylines).
- **Examples**:
  - Input: `examples/occlusion2.csv`
  - Expected Output: `examples/occlusion2_sol.csv`

## Methodology

### 1. Data Input and Preprocessing
- Polylines are read from CSV files and preprocessed for regularization and symmetry detection.

### 2. Curve Regularization
- The regularization process smooths polylines while preserving geometric properties like curvature and symmetry.

### 3. Symmetry Detection
- Symmetry detection identifies axes or points of symmetry, helping in the reconstruction of missing parts of shapes.

### 4. Shape Completion
- For occluded and fragmented shapes, the completion process reconstructs the shape by extrapolating existing polylines.



## Libraries Used

- **NumPy**: 
  - Used for numerical operations on arrays, including reading CSV data and performing calculations on geometric shapes.

- **SciPy**:
  - Utilizes `scipy.spatial.ConvexHull` for convex hull computations and `scipy.ndimage` for image processing tasks.
  - `scipy.optimize.minimize` is used for optimization tasks, and `splprep` and `splev` from `scipy.interpolate` are used for spline fitting.

- **Matplotlib**:
  - Used for plotting and visualizing geometric shapes and paths.

- **OpenCV (cv2)**:
  - Used for image processing, including tasks related to shape detection and manipulation.

- **Scikit-image** (`skimage.measure.EllipseModel`):
  - Used for fitting an ellipse to a set of points, often in regularization tasks.

- **Shapely**:
  - Used for geometric operations on shapes, such as unions and validity checks (`unary_union`, `make_valid`).

- **SVG Libraries**:
  - **svgwrite**: Used for writing SVG files, specifically for converting polylines to SVG format.
  - **cairosvg**: Used for converting SVG to PNG (`svg2png`).

## Algorithms Used

- **Ramer-Douglas-Peucker (RDP) Algorithm**:
  - Simplifies polylines by reducing the number of points, used in functions like `apply_rdp` and `rdp_simplify`.

- **Convex Hull Calculation**:
  - Calculates the convex hull of a set of points, implemented via `ConvexHull`.

- **Ellipse Fitting**:
  - Uses `EllipseModel` from `skimage.measure` to fit an ellipse to a set of points.

- **Bezier Curve Fitting**:
  - Uses `splprep` and `splev` from `scipy.interpolate` to fit cubic Bezier curves to polylines.

- **Shape Regularization**:
  - Functions like `regularize_rectangle`, `regularize_circle`, and `regularize_ellipse` adjust and smoothen shapes to conform to specific geometric properties.

## Functions

- **Polyline to SVG Conversion**:
  - `polylines2svg`: Converts polylines to SVG format for visualization.

- **RDP Simplification**:
  - `apply_rdp`, `rdp_simplify`: Apply the RDP algorithm to simplify polylines.

- **Geometric Regularization**:
  - `regularize_rectangle`, `regularize_circle`, `regularize_ellipse`, etc.: Functions that regularize various geometric shapes.

- **Shape Identification and Processing**:
  - `identify_shape`, `group_fragments`, `fill_occlusions`: Functions used to identify, group, and process shapes from fragmented polylines.

- **SVG and Image Handling**:
  - `svg2png`: Converts SVG files to PNG format.

## How to Run

1. Ensure all required libraries are installed:
   ```bash
   pip install numpy scipy matplotlib opencv-python scikit-image shapely svgwrite cairosvg


## Results

- **Isolated Curves**: Output curves are smoother and exhibit enhanced symmetry.
- **Fragmented Shapes**: The process effectively combines fragmented polylines into unified, symmetric shapes.
- **Connected Occlusion**: The shape is regularized into a single, connected polyline.
- **Disconnected Occlusion**: Fragmented paths are reconnected to form a complete shape.

## Future Work

Future work will focus on enhancing the pipeline to handle raster images directly, converting them into polylines, and exploring advanced shape recognition techniques.

## Conclusion

This project successfully demonstrates the regularization and symmetry detection of 2D curves represented as polylines, providing a foundation for further development in shape recognition and processing.

