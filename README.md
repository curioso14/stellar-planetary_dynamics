# Computational Astrophysics — Planetary & Stellar Dynamics

A collection of computational astrophysics projects covering orbital mechanics, N-body simulations, galactic dynamics, and exoplanet science. Each report includes full derivations alongside the Python code used to produce the results.

**Course:** ASP5107 – Dynamics of Stellar and Planetary Systems · Pontificia Universidad Católica de Chile  
**Instructor:** Prof. Cristóbal Petrovich  
**Stack:** Python · Rebound · Reboundx · Gala · Astropy · NumPy · Matplotlib

---

## Projects

| # | Project | Topics |
|---|---------|--------|
| 1 | [Restricted Three-Body Problem — Lagrange Points & Jupiter Shepherding](#1-restricted-three-body-problem--lagrange-points--jupiter-shepherding) | Tadpole & horseshoe orbits, mean-motion resonances, Grand Tack hypothesis |
| 2 | [Orbital Dynamics & Plummer Potential — Omega Centauri and Galactic Orbits](#2-orbital-dynamics--plummer-potential--omega-centauri-and-galactic-orbits) | Plummer & Miyamoto-Nagai potentials, escape velocity, epicyclic frequencies |
| 3 | [Exoplanet Transit Geometry, Radial Velocities & Two-Planet Dynamics](#3-exoplanet-transit-geometry-radial-velocities--two-planet-dynamics) | Transit probability, Delaunay variables, RV curves, secular evolution |
| 4 | [Kozai-Lidov Mechanism & Mean-Motion Resonances](#4-kozai-lidov-mechanism--mean-motion-resonances) | Kozai-Lidov oscillations, critical inclination, phase space portraits |

---

## 1. Restricted Three-Body Problem — Lagrange Points & Jupiter Shepherding

**Tools:** Rebound · Reboundx · NumPy · Matplotlib

N-body simulations of the restricted three-body problem centered on the L4 Lagrange point and Jupiter-driven asteroid dynamics.

**Part 1 — Lagrange point dynamics:**
- Tadpole orbit around L4 for a test particle placed 60° ahead of a Jupiter-mass planet
- Gradual increase of test particle semi-major axis (1.00–1.05 AU): transition from tadpole to horseshoe orbit and eventual escape to L3/L5
- Gradual increase of planet mass (0.001–0.021 M☉): widening orbits and loss of stability above ~0.02 M☉
- Bonus: horseshoe orbit setup using Ω, ω, inc parameters

**Part 2 — Jupiter shepherding hazardous asteroids (Grand Tack hypothesis):**
- Inward migration of Jupiter with τ_a = 10⁵ yr using Reboundx
- Capture into 2:1 mean-motion resonance at ~11,700 yr; critical angle libration confirmed
- Eccentricity pumping and pericenter evolution until asteroid-Earth collision potential at Jupiter a_J = 3.41 AU
- Analytical verification using the conserved quantity √a(1 + (m−1)[1−√(1−e²)])
- Bonus: outward migration — resonance encounter without capture

---

## 2. Orbital Dynamics & Plummer Potential — Omega Centauri and Galactic Orbits

**Tools:** Gala · Astropy · NumPy · Matplotlib

Orbit integration in spherical and disk potentials applied to Omega Centauri and the Milky Way.

**Part 1 — Plummer potential (Omega Centauri, M=4.05×10⁶ M☉, b=26 pc):**
- Circular orbit at r₀=10 pc; escape velocity calculation: v_esc = 35.4 km/s
- Orbit families for r₀ = {0.2, 20, 200} pc and v₀ = {0, 0.25, 0.75, 0.95} v_esc
- 1D harmonic oscillator behavior for radial-only initial conditions
- Rosette orbits with decreasing eccentricity as v₀ → v_circ

**Part 2 — Miyamoto-Nagai potential (Milky Way disk, M=6.8×10¹⁰ M☉):**
- Solar neighborhood orbit integration: R₀=8000 pc, z₀=100 pc, v_R=5 km/s
- XY and XZ projections; cylindrical (ρ, z) representation
- Epicyclic frequencies κ and ν computed analytically and compared against numerical integration — excellent agreement

---

## 3. Exoplanet Transit Geometry, Radial Velocities & Two-Planet Dynamics

**Tools:** Rebound · NumPy · Matplotlib · Analytical derivations

Analytical and numerical study of transiting exoplanets and two-planet secular dynamics using the HAT-P-13 system.

**Part 1 — Transit geometry:**
- Transit condition derived in Cartesian and orbital element frames
- Transit probability for elliptical orbits: P(f) = R★(1 + e cos f) / a(1−e²)
- Keplerian-averaged probability: ⟨P⟩ = R★/a = GM R★/L²
- Orbit-averaged oblate star potential at quadrupolar order; full Hamiltonian in Delaunay variables

**Part 2 — HAT-P-13 system:**
- Transit probabilities: P(b) = 18.7%, P(c) = 0.68%; joint probability under independent and coplanar assumptions
- Rebound RV simulation over 3 years for planets b and c separately and combined; comparison with analytical amplitudes

**Part 3 — Two-planet secular evolution:**
- 100-year integration with f=Ω=I=0, ω=π/2: semi-major axis conserved, eccentricity shows secular increase
- Perturbation at a_b = 0.2 AU: onset of strong oscillations and eccentricity growth after ~20 years

---

## 4. Kozai-Lidov Mechanism & Mean-Motion Resonances

**Tools:** Rebound · NumPy · Matplotlib · Analytical derivations

Numerical and analytical exploration of the Kozai-Lidov (KL) effect for a test particle perturbed by an outer planet.

**Setup:** Test particle at a=1 AU, e=0.1, ω=60°; outer planet at a=5 AU, m=0.01 M☉; τ_sec ≈ 2680 yr → t_max = 10 τ_sec = 26,800 yr

**Results:**
- I=30° (below critical angle ~39.2°): eccentricity nearly constant — KL oscillations forbidden
- I=50°: moderate oscillations, e_max ≈ 0.558; orbit librating in ω-e phase space
- I=80°: strong oscillations, e_max ≈ 0.975, pericenter approaching 0; orbit librating
- Analytical e_max = √(1 − 5/3 cos²I) confirms numerical results
- Collision with the star requires I → 90° (e_max → 1, pericenter → 0)
- Phase space portraits in ω-e: circulation for I=30°, libration for I=50° and I=80°

> Each PDF contains the full written analysis together with the Python code used to produce all figures.

---

## Repository Structure

```
experimental-astrophysics/
├── README.md
├── restricted_3body_lagrange_jupiter_shepherding.pdf
├── orbital_dynamics_plummer_galactic_orbits.pdf
├── exoplanet_transits_radial_velocities_dynamics.pdf
└── kozai_lidov_mean_motion_resonances.pdf
```
