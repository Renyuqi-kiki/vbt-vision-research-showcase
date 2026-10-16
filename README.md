# Monocular Movement Analysis Prototype

A camera-based movement-analysis prototype with a small Python demonstration of trajectory processing, action phases, and quality checks.

**Start here:** [run the demonstration](#run-the-demonstration) · [system architecture](docs/system-architecture.svg) · [research records](https://github.com/Renyuqi-kiki/fitness-aqa-research-progress)

## Project context

This engineering project explored squat repetition detection and phase-aware summaries from a single camera. It provided the starting point for my later research on visual evidence and movement assessment.

This repository contains a focused demonstration rather than the complete private application. Physical velocity estimates have not been validated against a reference instrument; this is a research and educational prototype.

## System overview

![System architecture](docs/system-architecture.svg)

The undergraduate prototype followed this core processing chain:

1. Read a video or camera frame.
2. Estimate body or equipment locations in image coordinates;
3. smooth the vertical trajectory and identify movement phases;
4. segment repetitions with a state machine;
5. reject low-confidence or low-range-of-motion observations;
6. report interpretable per-repetition summaries.

## Synthetic demonstration

![Synthetic phase demonstration](docs/synthetic-phase-demo.svg)

The figure is generated from an illustrative synthetic trajectory. It contains no participant video or restricted dataset content.

## Run the demonstration

The small module in [`src/phase_teacher.py`](src/phase_teacher.py) demonstrates two ideas used in the research pipeline:

- converting a vertical image trajectory into coarse action phases;
- applying a quality gate before accepting a sequence for downstream analysis.

The code intentionally uses only the Python standard library so that the core logic remains easy to inspect.

```bash
python3 examples/run_demo.py
python3 -m unittest discover -s tests -v
```

Example output:

```text
quality.accepted=True
quality.valid_ratio=1.00
quality.rom_px=92.00
phases=standing,descending,descending,descending,bottom,ascending,ascending,ascending
```

## Repository boundaries

This public showcase deliberately excludes:

- participant or personal exercise videos and images;
- local databases and training CSV files;
- model weights and access credentials;
- private configuration and deployment details;
- Fitness-AQA, MyoMechanix, or any other restricted dataset files;
- claims of criterion validity against LPT, force plates, or motion capture.

The original engineering repository remains private. The code here is a small, independently organized teaching and research demonstration rather than a full copy of that system.

## Research context

Earlier project planning explored trajectory-derived supervision for temporal error localization. That direction is retained as project history, rather than a claim of a completed or validated method. Dated experiment summaries are available in the [research records](https://github.com/Renyuqi-kiki/fitness-aqa-research-progress).

## Limitations

Image trajectories depend on camera angle, distance, perspective, occlusion, pose-estimation noise, and frame timing. They require synchronized reference measurements before supporting physical-accuracy claims.

## Author

**Yuqi Ren**  
The Hong Kong Polytechnic University  
GitHub: [Renyuqi-kiki](https://github.com/Renyuqi-kiki)
