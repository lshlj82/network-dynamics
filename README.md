# Dynamics on networks: interactive demo

An interactive, browser-based companion to the lecture **“Dynamics”** (Chapter 7 of *A First Course in Network Science* by Menczer, Fortunato, and Davis). It lets students run the chapter’s spreading and opinion models step by step, change their parameters, and compare simulations with mean-field predictions.

Created by Claude Opus 5.5 based on the lecture slides by Sang Hoon Lee.

## Running it

Everything is in a single file, `index.html`. There is no build step and nothing to install.

- **Locally:** open `index.html` in any modern browser.
- **GitHub Pages:** push this repository, then go to *Settings → Pages*, set the source to the `main` branch (root folder), and the demo will be served at `https://<user>.github.io/<repo>/`.

Each model has its own address, so you can link straight to one from slides or a syllabus by adding its name after `#`. For example, `index.html#epi` opens the epidemic model.

| Section | Model | Link |
| --- | --- | --- |
| 7.1 Influence | Fractional threshold model | `#thr` |
| 7.1 Influence | Mean-field threshold analysis, r(t+1) = F(r(t)) | `#gra` |
| 7.1 Influence | Independent cascade model | `#ic` |
| 7.2 Epidemics | SI, SIS, SIR, and SIRS on networks | `#epi` |
| 7.2 Epidemics | Rumor spreading (ignorant, spreader, stifler) | `#rum` |
| 7.3 Opinions | Majority vs voter model on networks | `#vot` |
| 7.3 Opinions | Bounded-confidence model | `#bc` |
| 7.3 Opinions | Coevolution of networks and opinions | `#co` |

## What each model shows

**Threshold model.** A node adopts when the fraction of its active neighbors reaches its threshold θ. Click nodes to choose initial adopters, and add spread to the thresholds to see when cascades get blocked or go global.

**Mean-field threshold analysis.** Granovetter’s cobweb iteration on the cumulative threshold distribution F, with stable and unstable fixed points marked. It includes the slide example F(r) = ¾r² + ¼ and a sweep over σ that reproduces the jump near σ ≈ 0.122 for μ = 0.25.

**Independent cascade.** Each newly active node gets one chance to activate each inactive neighbor with probability p. Running 300 cascades from the same seeds shows how variable the outcome is.

**Epidemic spreading.** SI, SIS, SIR, and SIRS dynamics on random (Erdős–Rényi) or scale-free (Barabási–Albert) networks, plotted against the mean-field equations. It reports R₀ = β⟨k⟩/μ alongside the heterogeneous version β⟨k²⟩/(μ⟨k⟩), and a sweep compares outbreak sizes on random and scale-free networks.

**Rumor spreading.** Spreaders stop when they meet people who already know the rumor, so a fraction of the population never hears it.

**Majority vs voter.** Both rules on random, scale-free, or 2D lattice networks, with optional zealots and spontaneous opinion changes. Links between nodes that disagree are drawn dashed. An exit-probability experiment on the chosen network type shows the step function for majority dynamics and the diagonal for the voter model.

**Bounded confidence.** Continuous opinions in [0, 1] that interact only within the confidence bound ε. The trajectory plot shows clusters forming while the mean opinion stays constant.

**Coevolution.** The Holme–Newman model, where links rewire toward like-minded nodes with probability p and opinions are copied otherwise. The live layout shows the network splitting into communities.

## Implementation notes

- Plain HTML, CSS, and JavaScript drawn on `<canvas>`; no libraries or frameworks.
- Fonts (Instrument Sans and Source Serif 4) load from Google Fonts, with system fallbacks when offline.
- Networks are laid out with a Fruchterman–Reingold force-directed algorithm.
- Supports light and dark mode and works on phones.
- Simulations are stochastic, so results vary from run to run, and the small network sizes used for interactivity show finite-size effects (for example, a nonzero epidemic threshold on scale-free networks).

## References

General

- F. Menczer, S. Fortunato, and C. A. Davis, *A First Course in Network Science*, Cambridge University Press (2020), Ch. 7.
- P. Erdős and A. Rényi, “On random graphs I,” *Publicationes Mathematicae Debrecen* 6, 290–297 (1959).
- A.-L. Barabási and R. Albert, “Emergence of scaling in random networks,” *Science* 286, 509–512 (1999).
- T. M. J. Fruchterman and E. M. Reingold, “Graph drawing by force-directed placement,” *Software: Practice and Experience* 21(11), 1129–1164 (1991).

Threshold models and cascades

- M. Granovetter, “Threshold models of collective behavior,” *American Journal of Sociology* 83(6), 1420–1443 (1978).
- M. S. Granovetter, “The strength of weak ties,” *American Journal of Sociology* 78(6), 1360–1380 (1973).
- D. J. Watts, “A simple model of global cascades on random networks,” *PNAS* 99(9), 5766–5771 (2002).
- C. Shao et al., “The spread of low-credibility content by social bots,” *Nature Communications* 9, 4787 (2018).
- J. Goldenberg, B. Libai, and E. Muller, “Talk of the network: A complex systems look at the underlying process of word-of-mouth,” *Marketing Letters* 12(3), 211–223 (2001).
- D. Kempe, J. Kleinberg, and É. Tardos, “Maximizing the spread of influence through a social network,” *Proc. 9th ACM SIGKDD*, 137–146 (2003).

Epidemics and rumors

- W. O. Kermack and A. G. McKendrick, “A contribution to the mathematical theory of epidemics,” *Proc. R. Soc. Lond. A* 115, 700–721 (1927).
- R. Pastor-Satorras and A. Vespignani, “Epidemic spreading in scale-free networks,” *Physical Review Letters* 86, 3200–3203 (2001).
- R. Pastor-Satorras, C. Castellano, P. Van Mieghem, and A. Vespignani, “Epidemic processes in complex networks,” *Reviews of Modern Physics* 87, 925–979 (2015).
- J. Stehlé et al., “High-resolution measurements of face-to-face contact patterns in a primary school,” *PLoS ONE* 6(8), e23176 (2011).
- K. Choi, H. Choi, and B. Kahng, “COVID-19 epidemic under the K-quarantine model: Network approach,” *Chaos, Solitons & Fractals* 157, 111904 (2022).
- B. Wuyts and J. Sieber, “Mean-field models of dynamics on networks via moment closure: An automated procedure,” *Physical Review E* 106, 054312 (2022).
- D. J. Daley and D. G. Kendall, “Epidemics and rumours,” *Nature* 204, 1118 (1964).
- D. P. Maki and M. Thompson, *Mathematical Models and Applications*, Prentice-Hall (1973).
- Y. Moreno, M. Nekovee, and A. F. Pacheco, “Dynamics of rumor spreading in complex networks,” *Physical Review E* 69, 066130 (2004).

Opinion dynamics

- P. Clifford and A. Sudbury, “A model for spatial conflict,” *Biometrika* 60(3), 581–588 (1973).
- R. A. Holley and T. M. Liggett, “Ergodic theorems for weakly interacting infinite systems and the voter model,” *Annals of Probability* 3(4), 643–663 (1975).
- P. L. Krapivsky and S. Redner, “Dynamics of majority rule in two-state interacting spin systems,” *Physical Review Letters* 90, 238701 (2003).
- M. Mobilia, “Does a single zealot affect an infinite group of voters?” *Physical Review Letters* 91, 028701 (2003).
- C. Castellano, S. Fortunato, and V. Loreto, “Statistical physics of social dynamics,” *Reviews of Modern Physics* 81, 591–646 (2009).
- G. Deffuant, D. Neau, F. Amblard, and G. Weisbuch, “Mixing beliefs among interacting agents,” *Advances in Complex Systems* 3, 87–98 (2000).
- R. Hegselmann and U. Krause, “Opinion dynamics and bounded confidence: Models, analysis and simulation,” *Journal of Artificial Societies and Social Simulation* 5(3) (2002).
- P. Holme and M. E. J. Newman, “Nonequilibrium phase transition in the coevolution of networks and opinions,” *Physical Review E* 74, 056108 (2006).
