Title: Optimal Probe density for Brownian First-Passage Detection of Impurities: The Detection Caldera

A - Problem in one sentence
At what probe (polystyrene probe particle) does the added Brownian searcher stop speeding up the search and start hindering detection of the impurity (Brownian target)?

B - Outline
1. **Introduction -** Includes the background of the study, Langevin/MSD theory, definition of the ergodic product E, area fraction, WCA potential, the problem statement of the manuscript, the objective of this paper, and the scope with which we have worked.
2. **The detection challenge chapter -** We include here the Brownian motion history, the two ways to measure D (which we worked with in 2025 SPP and validating the LAMMPS simulation for this paper), first-passage theory, crowding and caging, LAMMPS, and the study gap.
3. **Methodology -** two-species particle mixture, six system sizes, damping parameter, three-stage LAMMPS protocol, Brownian verification, detection-time definition, ensemble statistics, Caldera model, violin plots.
4. **Results -** caldera shape, fitted optimum, variance, ergodic product, violin plots, fourtype typology for the caldera, agreement of diagnostics, sensitivity, complication for ideal theory, open questions, and findings.
5. **Summary and conclusion**
6. **Appendix A** includes the SPP papers from the 2025 and 2026 SPP conferences and the LAMMPS code.

C - Motivation
Detecting trace impurities, for example, rare pathogens or analytes, in crowded fluids is a practical problem in point-of-care microfluidics and colloidal diagnostics. It also mirrors how enzymes and signaling molecules find targets in a crowded cytoplasm. Standard first-passage (earliest detection) theory says N independent searchers find a target N times faster, so probe number looks like something to maximize as much as possible. Realistically thinking, probes are finite-sized and cannot overlap, so as area fraction rises they collide, this is also considering that the space is finite, so adding more probes should cage one another and slows down the search. Overloading a sample also wastes reagent and risks clogging. Yet existing theory does not say at what density extra probes stop helping, or whether the breakdown of the 1/Np law can be detected early. In this thesis, we test where that transition occurs and whether it depends on system size.

d. State of the art
Dilute first-passage theory gives the ideal law $\langle T \rangle \propto 1/Np$, which rests on ergodicity and non-interacting searchers (Redner; Benichou, Loverdo, Moreau and Voituriez; Condamin et al.). In that limit, the ergodic product $E=Np\langle T \rangle$ is flat. Soft matter work describes caging as packing approaches the colloidal glass transition (Weeks et al., 2000). In earlier work by our Brownian group and in 2025 SPP, we built a validated LAMMPS pipeline and a damping-aware protocol for diffusion coefficients (Cusi et al.; Balejado et al., 2025), plus a preliminary single-system density we submitted in SPP 2026 (Balejado, Tapang, Saloma, 2026). What's missing is a systematic sweep of a size-varying, two-species WCA mixture across probe densities and system sizes, locating the diffusion-limited to crowding-limited crossover.

e. Answer in one sentence
Detection time is minimized near 30% area fraction regardless of system size, and the ergodic product detects crowding earlier.

f. At least one  figure/table/result
1. mean detection vs. area fraction and number of probes in the system
2. ergodic product plot
3. violin plots

g. Abstract (Combine E and F)
Across six system sizes, Langevin simulations show  Brownian detection time minimized near 30% area fraction, well below close packing, independent of system size; the ergodic product flags crowding tens of probes earlier.

h. methodology
We used LAMMPS to simulate, each run is a 2D Langevin simulation in a periodically bounded square with 2.0 micrometer polystyrene probes serving as the searcher and a 1.0 micrometer foreign particle serving as the target (the density of both particles is 1050 kg/m^3, and the environment simulated with water at 298K temperature). Six sizes (Ntotal= 10,30,50,70,100,200, each with varying box side length L=8.0-35.9 micrometer) spanning about 12-48% area fraction of their respective boxes, with Np swept from 1 to 99% of Ntotal. Particles are first de-overlapped with a soft potential and compressed to the target box. They then run for 2.0s with WCA repulsion, using damping times of 0.262 microseconds (probe) and 0.1 microseconds (foreign), and 10 seeds per condition was used. Brownian motion is verified by Dmsd and Dvar against the stokes-Einstein relation. Detection occurs when any probe first comes within 1.5 micrometer of a foreign particle (minimum-image distance). The mean detection time ($\langle T \rangle$) is averaged over seeds, and each system's detection time versus Np is fitted with $a_{Np}^{-\alpha}+b_{Np}^{\beta}+c$$ by weighted least squares. The minimum gives Np*, which converts to $$\phi*$$ which is the optimal area fraction.

i. Problems met and adjustments
1. random starts overlapped, so a three-stage protocol was adopted which includes soft-potential relaxation, compression, then WCA. This is also to ensure that the simulation is grounded in reality/was thought from actual situations
2. Few Np points at small Ntotal blurred the minimum, motivating SEM-weighted fits and the Type I caldera label.

j. summary
This paper/thesis asks when adding Brownian probes stops accelerating detection of impurity. Using LAMMPS Langevin simulations of 2 micrometer probes searching for 1 micrometer foreign particles under WCA repulsion, it sweeps probe number across six system sizes (Ntotal = 10-200). Detection time always follows a caldera shape. A two-term fit places the optimum near the optimum area fraction of 29-31% for Ntotal=30-200, about 1/3 of the close-packing limit, so the breakdown is dynamical caging rather than lack of  space. The ergodic product flags crowding twenty to thirty probes earlier in the larger systems. Profiles are classified into four types. The limits currently are that we are working in 2D system, repulsion only, 10 seeds, and an unresolved system-size effect.