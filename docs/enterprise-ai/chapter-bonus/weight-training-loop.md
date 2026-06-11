---
layout: default
title: ACME Overview
nav_exclude: true
---

# Who Adjusts the Weights During AI Training?

One of the most common misconceptions about Large Language Models (LLMs) is that humans somehow "teach" the model by manually adjusting its knowledge.

That is not how modern AI training works.

Humans do **not** manually adjust model weights.

The learning process is fully automated and driven by mathematics, optimization algorithms, and massive GPU infrastructure.

---

# The Core Training Loop

Training can be summarized as:

```text
Prediction
    ↓
Error
    ↓
Correction
    ↓
Weight Update
```

This cycle is repeated billions or even trillions of times.

Conceptually:

```text
Initial Weights
    ↓
Training
    ↓
Continuous Adjustment
    ↓
Final Weights
```

The final weights represent everything the model has learned during training.

---

# Step 1: Start With Random Weights

A neural network consists of layers of interconnected neurons.

```text
Input
  ↓
Neurons
  ↓
Output
```

Every connection has an associated numerical value called a **weight**.

Example:

```text
Weight A = 0.12
Weight B = -0.44
Weight C = 0.89
```

In modern frontier models:

```text
100 Billion+
to
1 Trillion+
weights
```

Most of these weights are initialized randomly.

At this stage, the model knows nothing.

---

# Step 2: Make a Prediction

Suppose the training data contains:

```text
The capital of France is _____
```

The model attempts to predict the next token.

It might initially predict:

```text
London
```

The correct answer is:

```text
Paris
```

The prediction is wrong.

---

# Step 3: Measure the Error

The model uses a mathematical function called a **Loss Function** to calculate how wrong the prediction was.

Example:

```text
Prediction = London
Expected   = Paris

Loss = High
```

If the prediction had been:

```text
Pari
```

The loss would be lower because the prediction is closer to the correct answer.

The loss function produces a numerical score.

Example:

```text
Loss = 7.8
```

Higher loss indicates a worse prediction.

---

# Step 4: Identify What Caused the Error

This is where the real learning happens.

An algorithm called **Backpropagation** determines:

> Which weights contributed to the prediction error?

The model does not guess.

It calculates this mathematically.

For a model with billions of parameters, backpropagation traces the error through the network and estimates how much each weight influenced the mistake.

---

# Step 5: Compute Gradients

For every weight, the model calculates:

```text
If I change this weight slightly,
does the error improve or worsen?
```

The answer is called the **gradient**.

Example:

```text
Weight A should increase
Weight B should decrease
Weight C should remain nearly unchanged
```

The gradient provides a direction for improvement.

---

# Understanding Gradients: The Mountain Analogy

Imagine standing blindfolded on a mountain.

Your objective is to reach the lowest valley.

```text
Mountain Peak
      ↓
     Slope
      ↓
     Valley
```

You cannot see the valley.

However, you can feel the slope beneath your feet.

If the ground slopes downward toward the east, you take a step east.

You repeat this process continuously.

Eventually, you arrive near the lowest point.

Training works similarly.

The model uses gradients to determine which direction reduces the error.

The "height" of the mountain is the loss value.

The goal is to move toward lower loss.

---

# Step 6: The Optimizer Updates the Weights

Once gradients are calculated, an **Optimizer** performs the actual weight updates.

Common optimizers include:

```text
SGD (Stochastic Gradient Descent)
Adam
AdamW
```

The optimizer combines:

```text
Current Weight
+
Gradient
```

to produce:

```text
New Weight
```

Example:

```text
Old Weight = 0.12

Gradient = +0.03

New Weight = 0.15
```

No human involvement is required.

The optimizer automatically updates billions of weights simultaneously.

---

# The Complete Training Cycle

A single training iteration looks like:

```text
Training Data
      ↓
Predict Next Token
      ↓
Calculate Error
      ↓
Run Backpropagation
      ↓
Compute Gradients
      ↓
Update Weights
      ↓
Repeat
```

This cycle runs continuously across enormous GPU clusters.

The process may execute:

```text
Millions
to
Billions
of iterations
```

before training completes.

---

# What Are Humans Actually Doing?

Humans design and supervise the system, but they do not manually edit weights.

Their responsibilities include:

## 1. Designing the Architecture

Examples:

```text
Number of Layers
Attention Mechanisms
Embedding Dimensions
Context Length
```

## 2. Preparing the Training Data

Examples:

```text
Books
Web Pages
Research Papers
Code Repositories
Documentation
```

## 3. Configuring Training Parameters

Examples:

```text
Learning Rate
Batch Size
Optimizer Selection
Training Duration
```

## 4. Monitoring Progress

Examples:

```text
Is the loss decreasing?
Are benchmark scores improving?
Are there signs of overfitting?
```

Humans guide the process.

Mathematics performs the learning.

---

# Why Humans Cannot Adjust Weights Manually

Consider a frontier model with:

```text
1.8 Trillion Parameters
```

Manually editing those weights would be impossible.

Even if a person could modify one weight every second:

```text
1.8 Trillion Seconds
≈ 57,000 Years
```

for a single pass.

This is why learning must be automated.

---

# Where Is Knowledge Stored?

This is one of the most fascinating aspects of modern AI.

There is no individual weight that stores:

```text
France = Paris
```

Instead, knowledge is distributed across many weights.

Example:

```text
Weight #183928474
Weight #928374923
Weight #773829104
Weight #193847562
...
```

Together they contribute to concepts such as:

```text
France
Europe
Capitals
Geography
Language
History
```

Knowledge emerges from the interaction of billions of parameters.

---

# The Big Picture

The learning process can be visualized as:

```text
Random Neural Network
          ↓
Read Massive Amounts of Data
          ↓
Make Predictions
          ↓
Measure Mistakes
          ↓
Adjust Weights Automatically
          ↓
Repeat Billions of Times
          ↓
Useful Intelligence Emerges
```

The continuous adjustment of weights is performed by:

```text
Backpropagation
        +
Gradient Calculation
        +
Optimization Algorithms
        +
Massive GPU Compute
```

Not by humans.

Humans build the training system.

Mathematics performs the learning.

---

# Key Takeaway

A common misconception is that humans somehow "inject" knowledge into a model by manually teaching it facts.

In reality:

```text
Humans Design The System
            ↓
Training Data Feeds The System
            ↓
Mathematics Measures Error
            ↓
Backpropagation Finds Improvements
            ↓
Optimizers Update Weights
            ↓
Knowledge Emerges
```

The billions or trillions of weights inside a modern AI model are adjusted automatically through optimization algorithms running on massive GPU clusters.

Humans create the learning framework.

The model learns through repeated prediction, error measurement, and weight adjustment.