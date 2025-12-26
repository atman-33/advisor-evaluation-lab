# Advisor Evaluation Lab

This repository serves as a laboratory for evaluating and iteratively improving AI advisor agents. It implements an automated feedback loop where agents collaborate to refine a knowledge base, aiming to produce high-quality, empathetic, and effective advice.

## Overview

The project uses a multi-agent system to simulate an improvement cycle:

1.  **Advice Generation (Sub-B Agent)**: An advisor agent generates responses to a set of benchmark cases based on the current `knowledge/`.
2.  **Evaluation (Sub-A Agent)**: An evaluator agent scores the responses against expected criteria (empathy, logic, actionability).
3.  **Improvement (Sub-C Agent)**: Based on the evaluation feedback, an improver agent updates the `knowledge/` and configuration to address weaknesses.
4.  **Loop**: This process repeats to continuously enhance the advisor's performance.

## Repository Structure

- **`knowledge/`**: Contains the core guidelines and wisdom used by the advisor agent. This is the primary target for improvement.
- **`docs/`**:
    - `advice-benchmark-cases.md`: A collection of scenarios used to test the advisor.
    - `scores.yml`: A record of evaluation scores across different trials.
    - `trials/`: Detailed logs of each iteration, including generated responses and review reports.
- **`config.yml`**: Configuration file for the agents.

## Workflow

The Main Agent orchestrates the following loop:
1.  Check previous scores.
2.  Instruct Sub-C to improve knowledge (if not the first trial).
3.  Instruct Sub-A to run the evaluation.
4.  Commit changes if the score improves; rollback if it degrades.
