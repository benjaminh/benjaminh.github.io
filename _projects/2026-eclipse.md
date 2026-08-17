---
layout: page
title: 2026 Total Solar Eclipse
description: First attempt at capturing the Sun during 2026 total eclipse
img: assets/img/projects/2026-Eclipse/2026-08-12-1951_cartouche.jpg
importance: 1
category: fun
---

A solar eclipse occurs when the Moon positions itself between the Earth and the Sun, such that the three celestial bodies (Sun – Moon – Earth) align almost perfectly along an imaginary plane known as the ecliptic (see figure below).
A total solar eclipse occurs somewhere on Earth approximately every 18 months. However, for a specific location, the phenomenon can often span 300 to 400 years (source: [CNES](https://cnes.fr/dossiers/eclipses-solaires)).

The Moon’s shadow path across the Earth’s surface is called "the path of totality". This path rarely crosses mainland France, so most eclipses visible in France are partial. The most recent total solar eclipse visible in France occurred in August 1999, during which observers in the northern part of the country could witness totality.
More recently, a total solar eclipse occured on August 12, 2026. Although the path of totality only crossed Spain, an obscuration of over 90% was observable in some areas of France.


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/2026-Eclipse/Total_Solar_Eclipse_Graphics_En_01.svg" title="Solar Eclipse schema" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Graphical representation of Total Solar Eclipse - CC BY-SA SanuN
</div>


## Setup

I had previously attempted to photograph the Moon and a few planets (especially Saturn) with my simple setup, but capturing the Sun and eclipse phenomena proved to be more challenging.
I carefully selected an observation site with a clear view of the western horizon. The coast of Loire-Atlantique was the perfect location: I set up in Prefailles, France. Although I was not within the path of totality, we were still able to observe an obscuration of 96.3%.

Below is a description of the setup used to capture this event:

- Refractor: TSOptics TSMPT60 \| Focal ratio $$f/6$$
- Accessories: EuroEMC AstroSolar filter (**Do not, EVER, look at the sun without appropriate filter**) \| UV/IR Omegon filter
- Camera: ZWO ASI 585MC (Sensor size: 11.13 × 6.26 mm, Full resolution: 3840×2160 px, Pixel width: 2.9 $$\mu m$$)
- Capture software: ASICap

I use an equatorial mount without any GoTo or motorization. Therefore, I rely on manual tracking and the drift method to capture images:

1. Capture begins with the Sun at the edge of the camera’s sensor field of view.
2. Video recording continues until the Sun starts exiting the field of view.
3. Manually adjust the tracking to return to step 1.

Capture settings in ASICap:

- Image resolution with Region of Interest: 2540×1440 px
- Gain: 200
- Exposure: between 1 and 2 ms, depending on the eclipse stage
- Recording duration: 30 to 45 seconds
- FPS: 50 to 70

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/2026-Eclipse/20260812_194343.jpg" title="Final capture setup" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/2026-Eclipse/Screenshot-ASICAP-08-2026.png" title="ASICap screenshot" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: final hardware setup in Prefailles, France. Right: screenshot of ASICap software and capture parameters.
</div>

Post-processing:

- AutoStakkert4: This software is widely used in astrophotography to stack astronomical images. Out of the thousands of frames recorded, the software retains only the sharpest images, discarding those affected by atmospheric turbulence.
- Astrosurface: Once stacking is complete, Astrosurface provides image processing algorithms. The most important algorithm is wavelets, which applies frequency filters to reveal details in the stacked image.
- GIMP: Used only to create the final image assembly below.


## Results

From the dozens of video recordings made during the eclipse, I selected the most representative and highest-quality ones. After applying the post-processing steps, here is the final compilation of the eclipse stages:

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/2026-Eclipse/2026-08-12-Solar-Eclipse-Montage.jpg" title="Final photo editing of the solar eclipse | CC BY Benjamin Hervy" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
   Solar Eclipse | August 12, 2026 | Prefailles, France | CC BY Benjamin Hervy
</div>

Some of the photos clearly shows visible sunspots AR4507 and AR4508 !