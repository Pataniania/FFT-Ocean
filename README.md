# Unreal Engine FFT Ocean Simulation (WIP) 🌊

A high-performance, real-time ocean surface simulation implemented in Unreal Engine using **Fast Fourier Transform (FFT)** and **Niagara GpuCompute**. This project is based on the technical framework provided by the [DeathreyCG Ocean Simulation Tutorial](https://dev.epicgames.com/community/learning/tutorials/qM1o/unreal-engine-ocean-simulation).

![Project Status](https://img.shields.io/badge/Status-Work--In--Progress-orange)
![Unreal Engine](https://img.shields.io/badge/Unreal%20Engine-5.3+-blue)

---

## 📖 Overview
This project focuses on generating realistic, tiling wave displacements and spectral foam using the **Phillips Spectrum** approach. Unlike standard vertex displacement, this method calculates wave height and slope in the frequency domain and transforms them into the spatial domain using an Inverse FFT (IFFT) executed entirely on the GPU via Niagara.

## 🛠 Technical Implementation
The simulation follows a multi-stage pipeline within Niagara:
1. **Spectrum Population:** Generating initial amplitudes based on wind speed, direction, and fetch.
2. **Time Evolution:** Updating wave phases over time.
3. **IFFT Row/Column Passes:** Executing the butterfly stages of the FFT to get displacement data.
4. **Render Target Export:** Using `SetRenderTarget` to write the simulation results (Height, Displacement, Normals) into textures for the Ocean Material.

## 🚀 Getting Started
### Requirements
* **Unreal Engine 5.6** or higher.
* **Plugins Enabled:** Niagara, Niagara Fluids (for Grid2D support).

### Setup
1. Clone the repository into your `Content` folder.
2. Open `M_Ocean_Master` to view the material implementation.
3. Ensure the Niagara System `NS_Ocean_Simulation` is active in the scene to drive the Render Targets.

---

## 🪵 Development Logs (Dev Logs)

### [2026-03-08] - Initial Setup & RT Pipeline
* **Progress:** Successfully implemented the Niagara Emitter structure.
* **Current Task:** Working on the ` Spectrum generation stage` 

### [Planned Updates]
- [ ] Implement Horizontal/Vertical IFFT passes.
- [ ] Add Cascaded Grids for distant ocean detail.
- [ ] Integrate Spectral Foam based on Jacobian determinants.
- [ ] Optimize Render Target usage for mobile/low-end scalability.

---

## 📚 Credits
* **Tutorial:** [DeathreyCG (Epic Games Dev Community)](https://dev.epicgames.com/community/learning/tutorials/qM1o/unreal-engine-ocean-simulation)
* **Math:** Based on Jerry Tessendorf's "Simulating Ocean Water" research.

---

## ⚖️ License
This project is for educational purposes. Refer to the original tutorial for specific licensing regarding the simulation logic.
