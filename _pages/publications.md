---
layout: page
permalink: /publications/
title: Research
description: Published articles, forthcoming work, revisions, and selected preprints.
nav: true
nav_order: 1
---

{% include bib_search.liquid %}

<div class="publications">

<h2>Published &amp; forthcoming</h2>

{% bibliography --query @*[submission_stage=revision] %}

{% bibliography --query @*[status=accepted] %}

{% bibliography --query @*[status=published] %}

<h2>Selected preprints</h2>

{% bibliography --query @*[status=manuscript && submission_stage!=revision] %}

</div>
