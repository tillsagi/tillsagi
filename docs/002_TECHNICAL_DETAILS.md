# 002 Technical Details of Tills AGI Implementation

## Overview

This document provides an in-depth look at the simulation code, scoring mechanisms, and feedback integration that underpin the Tills AGI framework. The implementation demonstrates how composite cognitive units (Tills) are defined, evaluated, and updated in real time to drive decision-making. As part of our Proof-of-Concept (POC), we are developing a local version that can run entirely on a developer's workstation, showcasing the framework's core capabilities.

## Simulation Code and Structure

The simulation is implemented in Python and comprises two primary classes: `Action` and `Till`.

### The Action Class

The `Action` class encapsulates an activity the AGI might perform. Each action is characterized by:

- **Name:** A short identifier.
- **Description:** Details of the action.
- **Effect Strength:** A measure of how strongly the action might influence the system.

When the `execute()` method is called, the action prints its details and simulates an outcome value, which is then used for feedback.

### The Till Class

The `Till` class represents a composite cognitive unit that integrates:

- **Memory, Instinct, and Real-Time Input:** These represent stored experiences, hard-wired responses, and immediate sensory data, respectively.
- **Metadata:** Including context tags, objectives, goal priorities, and operational rules.

Each Till computes a **composite score** that determines its relevance based on:

- A **base score** computed from the weighted sum of memory, instinct, and real-time input.
- **Context Bonus:** Extra weighting if the Till’s stored contexts match the current decision context.
- **Objective Bonus:** Additional points if the Till’s objectives align with the AGI’s overarching goals.
- **Priority Bonus:** A value based on the inherent goal priority of the Till.

### Scoring Mechanism

The `score()` method in the `Till` class combines multiple factors:

- **Weighted Cognitive Inputs:** Memory, instinct, and real-time input are combined using specified weights.
- **Context Matching:** The method checks for overlaps between the Till's context tags and the decision context.
- **Objective Alignment:** It also matches the Till’s objectives with the AGI’s primary objectives.
- **Goal Priority:** The Till’s priority is factored in as a bonus.

This composite scoring ensures that the most relevant Till is selected for a given decision.

### Feedback Integration and Learning

After an action is executed, feedback is simulated to reflect the outcome. This feedback includes:

- **Reward Value:** Derived from the execution outcome.
- **Feedback Notes:** Qualitative information on the performance.
- **Indicator for Creating New Tills:** In cases of high reward, suggesting that new cognitive units may be needed.

The `update_till()` function then adjusts the Till’s cognitive parameters slightly toward the feedback values, and the feedback is stored in the Till’s metadata. This mechanism models continuous learning and adaptation, ensuring that the AGI refines its decision-making over time.

## Local Proof-of-Concept (POC) Development

We are actively developing a POC that can be run entirely on a local developer's workstation. This POC will integrate:

- A lightweight neural network encoder (using PyTorch or TensorFlow) to generate embeddings for Tills.
- Virtual representations of robotic and IoT devices that simulate sensory inputs, such as visual data, audio signals, and environmental sensor readings.
- Demonstrations of both "awake" (real-time decision-making) and "dream" (offline consolidation and simulation) states to showcase dynamic feedback loops and adaptive learning.

The goal is to provide a high-level demonstration of the Tills AGI framework that is accessible and executable on common hardware, paving the way for deeper exploration and refinement in subsequent development phases.

### To be continued...

<< [001 Introduction to the Tills Framework and Motivation](./001_INTRODUCTION.md) | [003 Neural Network Enhancements for Tills AGI](./003_NEURAL_NETWORK_ENHANCEMENTS.md) >>
