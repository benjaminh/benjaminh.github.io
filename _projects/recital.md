---
layout: page
title: Recital
description: Ongoing crowdsourcing project about Comédie-Italienne
img: assets/img/projects/Recital/recital-home.png
importance: 2
category: work
---

During a post-doc at [Polytech Nantes](https://polytech.univ-nantes.fr/), I worked on crowdsourcing project called Recital. This project aims at transcribing 25 000 pages from a XVIII<sup>th</sup> century corpus related to the Comédie Italienne accounting. Due to the diversity of pages (format, writing, etc.), machine learning methods fail to perform good accuracy on optical character recognition and labelling. However, labelling and transcribing text from image is particularly suited to HITs (Human Intelligence Task), and that's why we investigated crowdsourcing.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/Recital/recital-home.png" title="Homepage of the Recital website" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/Recital/recital-example.png" title="Screenshot of an accounting daily page to be labeled and transcribed" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/Recital/recital-activity.png" title="Figure of the workers activity on Recital platform since the launch in 2017" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    On November 2021, the platform had registered more than 1 million contributions from +1800 workers. It is interesting to note that stimulating activity was not so easy (newsletter, forum, remote hackathons, etc.).
</div>

Under the supervision of Guillaume Raschia, I investigated the ETL (Extract-Transform-Load) pipeline to process workers' contribution through our dedicated web platform. My work included natural language processing, databases, data visualization, and web development among other things.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/Recital/recital-dashboard-1.png" title="Screenshot of the Recital dashboard with the final visualization" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/Recital/recital-dashboard-2.png" title="Screenshot of the Recital dashboard with statistics and faceting search" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Once the processing pipeline and the database are in place, we can design a dashboard to provide analytics and data visualizations. This part of the work was mainly done by colleague Olivier Aubert.
</div>

Most of the work consisted in developing processing algorithms involving data matching or natural language processing techniques to perform entity recognition or quantifying output data quality. In addition, we worked on data traceability to provide final experts some insights on the whole processing pipeline, from the original source to the reconstructed values.
