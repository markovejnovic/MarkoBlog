---
title: "The frequency response of the MXR Microamp amplifier"
date: 2018-07-28T00:00:00+02:00
draft: false
---

The full paper is available for download
[here](https://github.com/markovejnovic/freq-response-microamp/raw/master/tex/freq-response.pdf).
A small excerpt is given below.

Please visit the [GitHub
repository](https://github.com/markovejnovic/freq-response-microamp) for more
information.

## Explanation

This paper was a research article done as an attempt for my mock physics
internal assessment, however, it was rejected, due to being "out of syllabus".
Again, I did this out of love for electronics.

# Introduction

Frequency response is a measure of how much a certain circuit alters the
amplitude of an input sine signal with respect to the frequency of the signal.
A flat frequency response is one where the output signal is amplified by a
constant value, independent of the frequency of the input signal.

This amplifier pedal advertises itself as having a flat frequency response. The
research goal of this paper is to determine the frequency response of the
pedal. Other studies have determined that the frequency response is, indeed,
flat.

# Method

A copy of the _MXR Microamp_ was assembled on a breadboard.

![Assembled
Microamp](https://github.com/markovejnovic/freq-response-microamp/raw/master/tex/img/mxr-microamp-used.png)

The assembled circuit was connected to a computer with sine-wave generating
capabili- ties via a _3.5mm jack_ on the computer. At the output it was
connected to an oscilloscope, which was set to automatically measure the data
every two seconds. The recorded data was then copied to a computer which did
the data processing. A program on the com- puter enabled the sine-wave
frequency to be automatically increased by a fixed value of _25Hz_.

# Data

## Raw data

The oscilloscope recorded a total of 23376000 different voltage points for
varying frequencies. It is available at the [GitHub
repository](https://github.com/markovejnovic/freq-response-microamp).

## Data processing

An algorithm available at the [GitHub repository](https://github.com/markovejnovic/freq-response-microamp) was employed to achieve sinusoidal fits for each individual frequency. The amplitude was calculated.

![Fit](https://github.com/markovejnovic/freq-response-microamp/raw/master/tex/img/process1-example.png)

Finally, the amplitudes over the frequencies were plotted.

![Frequency
response](https://github.com/markovejnovic/freq-response-microamp/raw/master/tex/img/freq-response-v-log.png)

This is the final frequency response.

# Analysis

This is satisfactorily flat, since an electric guitar's frequencies mostly lie
between _80Hz_ and _1200Hz_.
