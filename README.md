# GenAI-Assisted-MOSFET-Characterization-and-TCAD-Diagnostics
A runnable student project for MOSFET transfer-curve characterization, anomaly
triage, and evidence-based TCAD experiment planning. Deterministic Python code
computes electrical metrics and compares curves. An optional GenAI explanation
turns those results into a readable engineering report; it does not invent
measurements, diagnose a unique physical root cause, or run Sentaurus.
Status: Working analysis prototype. The included datasets are synthetic
demonstrations, not Sentaurus runs or silicon measurements.


The key design choice is to calculate metrics with deterministic code and use
GenAI to explain the evidence and suggest follow-up checks. It does not ask a
language model to estimate threshold voltage from a picture of a curve.
What it does
1. Imports long-form Id–Vg data at one or more drain biases. A tabular
   Sentaurus/Inspect export can be mapped to the canonical CSV format.
2. Extracts constant-current threshold voltage, subthreshold swing, on/off
   currents, Ion/Ioff, peak transconductance, and DIBL when the data permit.
3. Flags patterns worth investigating and proposes specific device/model/mesh
   comparisons. Each diagnosis is a hypothesis tied to a numerical observation.
4. Ranks candidate simulated curves against a reference by RMS error in
   log10(|Id|) (decades), using only overlapping voltage ranges and matching
   drain biases.
5. Shows interactive plots and exports a Markdown report in the web app. An
   offline command-line path exports JSON and a PNG without an API key.
Run locally
Python 3.10+ is required. Run the commands from the repository root.
