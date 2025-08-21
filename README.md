# PTV-restitution-coefficient-home-experiment
This repository contains a home experiment to measure the coefficient of restitution of a bouncing object using Particle Tracking Velocimetry (PTV) and image processing. It covers circle finding / PTV fundamentals experimental setup &amp; analysis.  
# Particle Tracking Velocimetry (PTV) – Restitution Coefficient Home Experiment


## 🎯 Objectives
1) Build a robust PTV pipeline to extract position–time data of a bouncing object from video.  
2) Compute the restitution coefficient from impact velocities.  
3) Develop an empirical model and a calibrated DEM model and compare trajectories vs. experiment.

---

## Experimental Design (Home Setup)
- **Object:** e.g., ping-pong ball (good contrast, minimal deformation).  
- **Background:** matte black board for high contrast.  
- **Surface:** flat, rigid surface (e.g., granite worktop).  
- **Filming:** phone at 120 fps (if available), fixed tripod, perpendicular angle to reduce perspective error.  
- **Lighting:** diffuse light to avoid motion blur/shadows.  
- **Scale reference:** ruler or checkerboard in frame for pixel → metre calibration.  
- **Trials:** multiple drop heights
_These choices are justified for contrast, reproducibility, and ease of calibration._

---

## Methods (PTV & Circle Finding)
- **Preprocessing:** grayscale → blur → threshold/adaptive threshold → morphology (optional).
- **Detection:** circle finding (e.g., HoughCircles) or contour detection with size/roundness filter.
- **Tracking:** frame-by-frame centroid extraction (single target → nearest-neighbour is sufficient).
- **Calibration:** pixels → metres using in-frame scale.
- **Kinematics:** differentiate position to get velocity; smooth with Savitzky–Golay if needed.
- **Restitution (e):** \( e = \frac{|v_{\text{after impact}}|}{|v_{\text{before impact}}|} \) using vertical velocity immediately pre/post impact.
- **Uncertainty:** timing resolution, pixel quantisation, perspective, lens distortion (brief discussion).

---

## Deliverables
- **Trajectory plots** (y vs. t) with detected bounce points.  
- **Velocity–time plot** around impacts.  
- **Distribution/mean ± SD** of restitution across heights.  
- **Sensitivity** to timestep/frame-rate & threshold parameters.  
- **Short discussion** vs. literature values (ping-pong ~0.8–0.9; rubber varies with surface).

---

## Empirical & DEM Models
- **Empirical model:** fit e(h) or energy loss per impact; compare predicted apex heights to data.  
- **DEM model (calibrated):** point mass + contact model (e.g., linear spring–dashpot with tuned damping); integrate to generate synthetic trajectory.  
- **Comparison:** overlay **experiment vs. empirical vs. DEM** trajectories; discuss discrepancies (air drag, spin, frame blur, off-axis impacts).  
- **Reference** prior coursework (Portfolio 1) if using prior integrators.

---

