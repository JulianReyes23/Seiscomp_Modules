# Seiscomp_Modules
A suite of customizable modules for seismic event processing within the SeisComP framework, including magnitude calculation, event location, depth determination, and waveform analysis.

# SeisComP Custom Seismic Analysis Modules 🌍⚡

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![SeisComP Version](https://img.shields.io/badge/SeisComP-4.0+-green.svg)](https://www.seiscomp.de/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-yellow.svg)](https://python.org)

A suite of customizable modules for **real-time seismic event processing** within the SeisComP framework. Designed for flexibility and regional adaptability, these modules enhance magnitude calculation, event location, depth determination, and data validation.

---

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Modules](#modules)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Validation](#validation)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

---

## Overview 📌
This repository provides **custom SeisComP modules** to extend seismic data processing capabilities for regional networks. Key functionalities include:
- **Local Magnitude (\(M_L\))**: Amplitude-based calculations with regional calibration.
- **Hybrid Event Location**: Combines Geiger's algorithm and depth-phase constraints.
- **Depth Estimation**: Integrates inversion methods and phase time differences.
- **Real-Time Integration**: Works seamlessly with SeedLink and SeisComP's database.

---

## Features 🚀
- **Customizable Constants**: Adjust regional parameters (\(c\), \(k\)) via config files.
- **Automated Processing**: Triggers calculations on new event detection.
- **Data Validation**: Tools to compare results against historical catalogs (e.g., GEOFON, IRIS).
- **Cross-Platform**: Compatible with Linux-based SeisComP deployments.

---

## Modules 📦

### 1. Magnitude Module
- Implements \(M_L = \log_{10}(A) + c \cdot \log_{10}(R) + k\).
- Fetches amplitudes and distances from SeisComP's database.
- **[Code](src/magnitude_module.cpp)** | **[Config](config/magnitude_module.cfg)**

### 2. Location Module
- Hybrid approach: Geiger's inversion + depth-phase analysis (\(pP\), \(sP\)).
- Supports 1D/3D velocity models.
- **[Code](src/location_module.cpp)** | **[Config](config/location_module.cfg)**

### 3. Depth Module
- Uses \(P\)-\(pP\)/\(sP\) time differences for depth estimation.
- Validates against inversion results.
- **[Code](src/depth_module.cpp)**

### 4. Data Tools
- **SeedLink Integration**: `slinktool`-based data streaming.
- **Validation Scripts**: Python tools for synthetic/historical data testing.
- **[Scripts](scripts/)**

---

## Installation ⚙️

### Prerequisites
- SeisComP ≥ 4.0
- CMake ≥ 3.10
- Python ≥ 3.8 (for validation scripts)

### Steps
```bash
# Clone the repository
git clone https://github.com/your-username/seiscomp-custom-modules.git
cd seiscomp-custom-modules

# Compile and install
mkdir build && cd build
cmake .. -DSEISCOMP_ROOT=/path/to/seiscomp
make
make install

# Copy config files
cp ../config/*.cfg $SEISCOMP_ROOT/etc/
