# Project Brief: FOU-Centered Stereo-ToF Fusion on FPGA

This project explores how a Stereo-ToF depth estimation network can be designed
with FPGA deployment in mind from the beginning. The central idea is to keep the
model, quantization behavior, runtime contract, and RTL-visible verification
path aligned through a shared deployment boundary.

## Public Scope

The public-facing material is intentionally high level. It is suitable for a
resume, project portfolio, or early research preview, but it is not a
reproducibility package.

The project currently emphasizes:

- Stereo-ToF fusion for depth estimation.
- A lightweight FPGA-aligned operator framing.
- Progressive training through floating point, QAT, and StrictQAT stages.
- Export of deployment assets that can be consumed by FPGA-side runtime paths.
- Runtime/API contract alignment.
- RTL simulation and post-simulation closure for representative full-network
  verification.
- Qualitative depth reconstruction evidence from the deployment-facing path.

## Evidence Boundary

The strongest public claim is not a single accuracy number. It is the fact that
the project connects several normally separate stages:

1. algorithm training
2. strict quantized export
3. FPGA runtime consumption
4. RTL simulation
5. post-simulation verification
6. visual depth reconstruction inspection

This makes the work closer to a full deployment pipeline than to a standalone
neural-network experiment.

## Non-Public Material

The following material is intentionally withheld before publication:

- source code and scripts
- exact model topology tables
- training and export commands
- checkpoints, FPGA binaries, and packed parameter assets
- runtime layout rules and internal run names
- detailed RTL implementation and testbench internals

The full implementation is planned for release after paper acceptance.
