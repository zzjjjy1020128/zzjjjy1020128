# Project Brief: FOU-Centered Stereo-ToF Fusion on FPGA

This project explores how a Stereo-ToF depth estimation network can be designed
with FPGA deployment in mind from the beginning. The central idea is to keep
model design, quantized deployment behavior, runtime contracts, RTL-visible
verification, and board measurement aligned through one deployment boundary.

## Public Scope

The public-facing material is intentionally high level. It is suitable for a
resume, project portfolio, or early research preview, but it is not a
reproducibility package.

The project currently emphasizes:

- Stereo-ToF fusion for 160x160 depth estimation.
- A lightweight FPGA-aligned operator and accelerator path.
- FP32-to-PTQ/INT8 deployment with FPGA-consumable assets.
- Runtime/API contract alignment for board execution.
- RTL simulation and post-simulation closure for representative full-network
  verification.
- Vivado-routed implementation evidence on a ZU9EG-class FPGA target.
- Board-side runtime measurement and qualitative multi-scene depth outputs.

## Public Metrics

Current public-facing measurements:

| Metric | Value | Scope |
| --- | ---: | --- |
| FPGA runtime | 4.195 ms / 238.4 FPS | INT8 FOU-Acc at the reported 200 MHz FPGA operating point |
| FP32 depth accuracy | 31.08 mm MAE / 58.41 mm RMSE | Full local evaluation split, 240 samples |
| Board-vs-FP32 fidelity | 15.06 mm mean abs / 58.59 mm p95 abs | Representative S1-S5 board scene set |
| FPGA resource occupancy | LUT/FF/DSP/BRAM 71.33/20.76/53.37/52.69% | ZU9EG-class Vivado-routed implementation |
| Power estimate | 4.423 W | Vivado post-route on-chip estimate |
| Verification closure | 43-layer runtime contract, RTL/post-sim checks, and board latency-quality sync | Deployment-facing validation path |

## Evidence Boundary

The strongest public claim is not a single accuracy number. It is the fact that
the project connects several normally separate stages:

1. algorithm training and FP32 reference quality
2. quantized deployment asset export
3. FPGA runtime consumption
4. RTL simulation and post-simulation inspection
5. Vivado implementation and resource/power reporting
6. board runtime measurement
7. multi-scene visual depth-output inspection

This makes the work closer to a full model-to-board deployment pipeline than to
a standalone neural-network experiment.

## Non-Public Material

The following material is intentionally withheld before publication:

- source code and scripts
- exact model topology tables
- training and export commands
- checkpoints, FPGA binaries, and packed parameter assets
- runtime layout rules and internal run names
- detailed RTL implementation and testbench internals

The full implementation is planned for release after paper acceptance.
