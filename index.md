---
layout: default
title: Accueil
---

<section class="hero">
  <p class="hero__eyebrow">Amicale des Professionnels de Santé d'origine Béninoise en Guinée</p>
  <h1 class="hero__title">Un réseau de professionnels de santé, uni au service de l'entraide.</h1>
  <p class="hero__lead">
    L'APSBG rassemble les médecins, pharmaciens, infirmiers, sages-femmes et autres
    professionnels de santé d'origine béninoise exerçant en République de Guinée.
    Notre association favorise l'entraide, le partage d'expertise et le renforcement
    des liens entre ses membres.
    <!-- Texte à personnaliser : mission, historique, activités de l'association -->
  </p>
  <a href="{{ '/membres/' | relative_url }}" class="button">Voir le catalogue des membres</a>
</section>

<section class="stats">
  {% assign membres = site.data.membres %}
  {% assign domaines = membres | map: "domaine_competence" | uniq | compact %}
  <div class="stats__item">
    <span class="stats__number">{{ membres.size }}</span>
    <span class="stats__label">Membres inscrits</span>
  </div>
  <div class="stats__item">
    <span class="stats__number">{{ domaines.size }}</span>
    <span class="stats__label">Domaines de compétence représentés</span>
  </div>
</section>
