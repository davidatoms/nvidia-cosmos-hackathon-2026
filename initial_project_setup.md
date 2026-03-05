1. Pattern Recognition and State Description

  Feed a screenshot of your viewport into Reason2 and ask it to reason about
  what it sees. It could:

  - Identify live pattern types (gliders, oscillators, still lifes)
  - Describe the density and distribution of active regions
  - Classify whether the simulation is in a chaotic, stabilizing, or stable
  phase

  Your existing logging system could pipe generation frames directly to Reason2
  for per-tick analysis.

  ---
  2. Spatio-Temporal Prediction via Reasoning

  Reason2's core strength is spatial-temporal understanding. Given a sequence of
   Game of Life frames (as images or token-encoded grids), it could reason
  through chain-of-thought about what should happen next — effectively learning
  to apply GoL rules through reasoning rather than hard-coded logic.

  This is a different approach than the transformer predictor from the ideas
  note — instead of a trained upscaler, it's a reasoning model that narrates and
   predicts evolution.

  ---
  3. DLSS Quality Auditor

  Run DLSS SR on the right viewport, exact rendering on the left. Feed both
  viewport frames to Reason2 and ask:

  "What differences do you see between these two Game of Life states? Are any
  cells present in one that aren't in the other?"

  Reason2 could act as an automated artifact detector, flagging where DLSS
  hallucinated cells or dropped them — replacing manual visual inspection.

  ---
  4. Full Pipeline

  Simulation tick
        |
        v
  Render at low resolution
        |
        v
  DLSS SR upscale --> Right viewport display
        |
        v
  Reason2 analyzes upscaled frame
        |
        v
  Chain-of-thought: "Pattern X is a glider moving SE,
                     cell cluster Y appears hallucinated,
                     predicted next state is..."
        |
        v
  Correction signal fed back to simulation logger

  ---
  5. Dual-Viewport Comparison Reasoning

  Your "Unlink Viewports" mode is ideal here. Run two diverging simulations and
  have Reason2 reason about why they diverged from an identical seed —
  describing the butterfly effect in natural language with spatial grounding.

  ---
  The most immediately practical use is #3 — using Reason2 as a visual QA layer
  on top of DLSS output to automatically detect upscaling artifacts in the
  simulation frames.
