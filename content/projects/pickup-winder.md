---
title: "Pickup Winder"
date: 2015-03-12T00:00:00+02:00
draft: true
---

# Introduction
Since I wanted to make my own [Flying V](/projects/flying-v/) from scratch, I needed to wind its humbuckers. A quick back-of-the-envelope calculation proved that winding the humbucker coils by hand would not only make bad coils, but also be extremely time consuming. I needed to make a machine powered winder that could count the number of revolutions (as that number's quite important and defines what the pickups frequency response will be). I also thought it would be quite useful to have the winder automatically align the wire.

## Construction and Design
I did some research and found this [_Mojotone Pickup Winder_](https://www.stewmac.com/Luthier_Tools/Tools_by_Job/Tools_for_Electronics_and_Pickups/Pickup_building/Mojotone_Pickup_Winding_Machine.html) on _StewMac_. I liked the design - it seemed simple and robust:

<img src="https://img1.stewmac.com/product/images/20340/Mojotone_Pickup_Winding_Machine.jpg" alt="Mojotone Pickup Winder" style="display: block; width:300px; margin: 0 auto;"/>

However, I didn't really like the fact that this pickup winder wasn't able to align the wire while winding. The guy behind it was supposed to manually steer the wire.

I decided to grab a linear actuator from a broken CD reader to serve as the aligner in my design.

In the end I made the pickup winder similar to the _Mojotone_ one, but it had a CNC aligner:

![]()

## Electronics
The electronics was quite simple. I got an _Arduino UNO_, an _EasyDriver_ for the linear actuator stepper motor control, a random _H-Bridge_ for the winder motor and a small motor encoder to count the steps. I hooked 'em up and wrote a small script. Later on, I added an LCD and a few buttons to make everything look good.

## The code

The code's available on [GitHub]().

## Issues


