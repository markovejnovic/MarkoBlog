---
title: "Investigating the effect of pickup position on the harmonic response of
an electric guitar"
date: 2018-10-18T00:00:00+02:00
draft: false
---

The full paper is available for download
[here](https://github.com/markovejnovic/Pickup-Position-Effects/raw/master/tex/relation-pickup-distance.pdf). A small excerpt is given below.

Please visit the [GitHub
repository](https://github.com/markovejnovic/pickup-position-effects) for more
information.

## Explanation

This was my extended essay topic for my IB curriculum. I did it simply because
I sincerely enjoy electronics and music.

# Introduction

The position of electric guitar pickups determines the way an electric guitar
sounds. Depending on the position of the pickup the frequency response of a
plucked string will differ largely. The goal of this research paper was to
investigate the aforementioned effect and create a relationship between the
frequency response of the guitar and the pickup position.

# Method
When a Fourier transformation is ran on a waveform it produces a continuous
function of frequency, showing precisely amplitudes of frequencies. To explore
the relationship between the pickup position and the harmonic effects, it is
necessary to look at a three-dimensional graph where one axis is the
independent variable - the position of the pickup, and two dependent variables
- the frequency and the amplitude.

To measure the effect of pickup position on harmonics of the electric guitar,
an electric guitar with a movable pickup was constructed as shown in the
following picture.

![Constructed
Guitar](https://github.com/markovejnovic/Pickup-Position-Effects/raw/master/tex/img/constructed-guitar.png)

The pickup wires were connected to a _GW Instek GDS-1000A-U_ oscilloscope. The
ground wire was also connected to the bridge of the electric guitar and the
ground of the oscilloscope, to remove any potential noise that might occur.

![Schematic](https://github.com/markovejnovic/Pickup-Position-Effects/raw/master/tex/img/connection-schematic.png)

# Data
## Raw data
The data gathered was similar to the one given in the following image.

![Data](https://github.com/markovejnovic/Pickup-Position-Effects/raw/master/tex/img/wave-0-5-e.png)

Due to the nature of the experiment an extreme amount of data was collected and
is therefore omitted from this brief explanation.

## Data processing
The data processing is available at the [GitHub
repository](https://github.com/markovejnovic/pickup-position-effects).

In a nutshell, the data was ran through a _Fourier transformation_ and then
using specific algorithms, described in the paper, peaks were identified. These
peaks were then connected with relation to the distance of the pickup in order
to identify the relationship.

![Processed
data](https://github.com/markovejnovic/Pickup-Position-Effects/raw/master/tex/img/final-graph-c.png)

# Evaluation
A different perspective shows that this experiment was extremely inconclusive.

![Perspective](https://github.com/markovejnovic/Pickup-Position-Effects/raw/master/tex/img/final-graph-e.png)

This was due to three major possibilities:

* Poor harmonic identification due to the possibility of a poor algorithm
* Poor harmonic identification due to the possibility of sustain causing
  certain harmonics to shift in frequency as well as deteriorate
  inconsistently.
* Minor effects which could sum up (angle of picking not being constant,
  strength of picking not being constant, etc)
