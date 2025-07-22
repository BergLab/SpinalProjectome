# SpinalProjectome

**SpinalProjectome** is a MATLAB-based framework designed to simulate the spinal cord circuitry of a mouse. It enables detailed modeling of neuronal populations with diverse cell types, spatial projection biases, and network connectivity, providing a powerful tool for studying spinal cord dynamics.

---

## Overview

This framework allows you to:
- Define multiple neuronal cell types, each with specific properties and spatial biases.
- Build a spatially organized network reflecting the anatomy and projection patterns of the spinal cord.
- Run dynamic simulations with customizable inputs.
- Visualize neuronal activity through firing rates, spike rasters, and muscle-like signals (EMG).

---

## Requirements

- MATLAB (recommended version: X or higher)
- MATLAB toolboxes: (list specific toolboxes if applicable, e.g., Signal Processing Toolbox)
- Clone or download this repository and set your MATLAB path accordingly.

---

## Step-by-Step Usage

### 1. Instantiate Network Parameters

Create the container for all network parameters and cell types:

```matlab
MyNetwork = NetworkParameters();
```
---


### 2. Add Neuronal Cell Types
Use the method AddCelltype() to add neuron populations. When doing so, specify their spatial and projection biases, cell numbers, and connection properties:

```matlab
% Example: Adding a V2a-2 interneuron with spatial biases
MyNetwork.AddCelltype( Celltype.V2a_2, ...
    'bi', ...                % BiasRC: 'bi' (bilateral)
    'ven', ...               % BiasDV: 'ven' (ventral)
    'lat', ...               % BiasML: 'lat' (lateral)
    '', ...                  % BiasLayer: none specified
    'ipsi', ...              % BiasSegment: ipsilateral
    '', ...                  % BiasContraIpsi: none specified
    '', ...                  % Additional layer bias
    600, ...                 % LengthScale: spatial spread in micrometers
    'Gain', 0.7, ...
    'SynStrength', gc*1 );
```
---

### 2. Add Neuronal Cell Types
Use the method AddCelltype() to add neuron populations. When doing so, specify their spatial and projection biases, cell numbers, and connection properties:

```matlab
% Example: Adding a V2a-2 interneuron with spatial biases
MyNetwork.AddCelltype( Celltype.V2a_2, ...
    'bi', ...                % BiasRC: 'bi' (bilateral)
    'ven', ...               % BiasDV: 'ven' (ventral)
    'lat', ...               % BiasML: 'lat' (lateral)
    '', ...                  % BiasLayer: none specified
    'ipsi', ...              % BiasSegment: ipsilateral
    '', ...                  % BiasContraIpsi: none specified
    '', ...                  % Additional layer bias
    600, ...                 % LengthScale: spatial spread in micrometers
    'Gain', 0.7, ...
    'SynStrength', gc*1 );
```

### Available Bias Properties

| Property          | Description                                               | Possible Values / Explanation                         |
|-------------------|-----------------------------------------------------------|--------------------------------------------------------|
| `BiasRC`         | Rostrocaudal bias (orientation along the caudal-rostral axis) | `'cau'`, `'ro'`, or `''` (none)                  |
| `BiasDV`         | Dorsoventral bias (dorsal vs ventral position)               | `'dors'`, `'ven'`, or `''`                        |
| `BiasML`         | Mediolateral bias (medial vs lateral position)             | `'med'`, `'lat'`, or `''`                        |
| `BiasLayer`      | Laminar bias (connection in specific laminar layers)        | `'lam1'`, `'lam2'`, `'lam3'`, `'lam4'`, `'lam5'`, `'lam6'`, or `''` |
| `BiasSegment`    | Segment bias (e.g., `'T13'`, `'L1'`, `'S4'`)                 | e.g., `'T13'`, `'L1'`, `'S4'`                      |
| `BiasContraIpsi` | Contralateral vs Ipsilateral connection bias               | `'contra'`, `'ipsi'`, or `''`                     |
| `LengthScale` | Spatial standard deviation of projection spread (μm)	            | e.g., `500`, `600`
    |

---
