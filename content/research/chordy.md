---
title: "An algorithm for determining the composition of a musical chord using
Fourier transformations"
date: 2018-12-06T00:00:00+02:00
draft: false
---

The full paper is available for download
[here](https://github.com/markovejnovic/Chordy/raw/master/tex/chord-identification.pdf).
A small excerpt is given below.

Please visit the [GitHub repository](https://github.com/markovejnovic/Chordy)
for more information.

## Explanation

This was my final mathematics internal assessment topic for my IB curriculum. I
did it because of my love for computer science and music.

# Introduction

The research goal of this paper was to create a simple algorithm with decent
performance which allows for recognizing chords and the individual tones that
make them up. This simple algorithm could prove useful as a piece of a bigger
algorithm for identifying chord progressions in songs.

# Method

Given an input signal such as the one given in the following figure, the
algorithm operates in 4 distinct stages.

![Input](https://github.com/markovejnovic/Chordy/raw/master/tex/img/input-signal.png)

## Fourier transformation

A Fourier transformation is done on the input signal.

## Peak identification

Peak identification was done by cutting off values under a certain constant
cutoff value _c_. 

![Fourier](https://github.com/markovejnovic/Chordy/raw/master/tex/img/fourier-signal.png)

Finally, peaks are identified by taking the average of
neighboring values and then finding the value which has the highest distance
from the average.

## Note identification

With the frequencies identified, notes were identified using a lookup table.

## Chord identification

With the notes identified, it was possible to use another lookup table to
identify the chord being played.

# Evaluation

The algorithm worked well with small values of _c_ and deteriorated as _c_
increased.

![Algorithm
Success](https://github.com/markovejnovic/Chordy/raw/master/tex/img/success-rate.png)
