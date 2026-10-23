# Flaky Test Hunter

A Camillia camflow that hunts down flaky tests: it re-runs the test suite repeatedly to
reproduce the intermittent failure, isolates the root cause with hard toggle evidence,
then either fixes the flake or quarantines the test with a written justification.

## What it does

1. **Reproduces** the flake — baseline run, then repeated re-runs (single test, file,
   suite; shuffled order; parallel vs. serial) until the failure signature is captured.
2. **Diagnoses** the mechanism — shared state, ordering, timing, async leakage, external
   resources, randomness, environment — proven by toggling the failure on and off.
3. **Decides** fix vs. quarantine from the evidence (fix is the default; quarantine is
   containment, never the first choice).
4. **Resolves** the flake — minimal mechanism-level fix, or a convention-following
   quarantine annotated with signature, reproduction rate, mechanism, and task reference.
5. **Verifies** stability — the previously flaky tests pass repeated runs under the
   original failing conditions — then commits, pushes, and moves the task to review.

## How it triggers

Task-type camflow. Schedule a task that describes the flaky test (test name, suite,
observed failure, how often it was seen) with this camflow, or bind it to a task event
in your workspace trigger bindings.

## Install

Install from the Camillia Community Hub. The hub imports `camflow.yaml` into your
Camillia instance; no other files are required at runtime.

## License

MIT — Copyright (c) 2026 Camillia contributors. See [LICENSE](LICENSE).
