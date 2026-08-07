---
layout: default
title: Catalogue des membres
permalink: /membres/
---

<section class="page-intro">
  <h1>Catalogue des membres</h1>
  <p>Retrouvez ci-dessous l'ensemble des professionnels de santé membres de l'APSBG</p>
</section>

<section class="card-grid">
  {% assign membres = site.data.membres | sort: "nom" %}
  {% for m in membres %}
    {% include member-card.html membre=m %}
  {% endfor %}
</section>
