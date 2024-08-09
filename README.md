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

## Results

- **Isolated Curves**: Output curves are smoother and exhibit enhanced symmetry.
- **Fragmented Shapes**: The process effectively combines fragmented polylines into unified, symmetric shapes.
- **Connected Occlusion**: The shape is regularized into a single, connected polyline.
- **Disconnected Occlusion**: Fragmented paths are reconnected to form a complete shape.

## Future Work

Future work will focus on enhancing the pipeline to handle raster images directly, converting them into polylines, and exploring advanced shape recognition techniques.

## Conclusion

This project successfully demonstrates the regularization and symmetry detection of 2D curves represented as polylines, providing a foundation for further development in shape recognition and processing.

