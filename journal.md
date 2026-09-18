---
layout: default
title: Journal
nav: journal
permalink: /journal/
---

<section class="page-intro">
  <div class="eyebrow">PUBLICATION</div>
  <h1>Journal</h1>
</section>

<section class="journal-page">

  <!-- Publication Statistics -->
  <div class="journal-stats">
  
    <!-- 전체 논문 -->
    <div class="journal-stat">
      <strong>02</strong>
      <span>Journal Papers</span>
    </div>
  
    <!-- International: 클릭 시 해당 섹션으로 이동 -->
    <a href="#international" class="journal-stat journal-stat-link">
      <strong>02</strong>
      <span>International Journal</span>
    </a>
  
    <!-- Domestic: 클릭 시 해당 섹션으로 이동 -->
    <a href="#domestic" class="journal-stat journal-stat-link">
      <strong>00</strong>
      <span>Domestic Journal</span>
    </a>
  
  </div>

  <!-- Search -->
  <div class="journal-search">
    <input
      type="search"
      id="journal-search"
      placeholder="Search by title, author, or journal..."
      aria-label="Search publications"
    >
  </div>

  <!-- International Journal -->
  <section class="journal-section" id="international">

    <div class="journal-section-header">
      <h2>International Journal</h2>
      <span>2 Papers</span>
    </div>

    <div class="journal-year-group">

      <h3 class="journal-year">2026</h3>

      <!-- 2026 Paper 1 -->
      <article class="journal-paper">

        <div class="journal-badges">
          <span>Journal</span>
          <span>International</span>
          <span class="highlight">Editor's Choice</span>
        </div>

        <h4>
          <a href="https://doi.org/10.1016/j.ijmedinf.2026.106505"
             target="_blank"
             rel="noopener noreferrer">
            Clinical Text Embeddings: A Systematic Review of Methods, Applications, and Future Directions
          </a>
        </h4>

        <p class="journal-authors">
          Hyunwoo Jo, <strong>Seon Kim</strong>, Hyunwoo Son, Jongchan Kim*
        </p>

        <p class="journal-name">
          International Journal of Medical Informatics, 2026 Sep
        </p>

      </article>

      <!-- 2026 Paper 3 -->
      <article class="journal-paper">

        <div class="journal-badges">
          <span>Journal</span>
          <span>International</span>
        </div>

        <h4>
          <a href="https://doi.org/10.1038/s41598-026-66283-w"
             target="_blank"
             rel="noopener noreferrer">
            Personalized Disease Prediction Framework based on Genomic Variants and Disease Histories using Deep Embeddings and Alignment-based Process Conformance Checking
          </a>
        </h4>

        <p class="journal-authors">
          Daewoo Pak, <strong>Seon Kim</strong>, Hyunwoo Jo, Jongchan Kim*
        </p>

        <p class="journal-name">
          Scientific Reports, 2026 Aug
        </p>

      </article>

      <!-- 2026 Paper 3 -->
      <article class="journal-paper">
      
        <div class="journal-badges">
          <span>Journal</span>
          <span>International</span>
        </div>
      
        <h4>
          <a href="https://doi.org/10.13104/imri.2025.0038"
             target="_blank"
             rel="noopener noreferrer">
            Segmentation-Based Landmark Localization in Cerebral
            Magnetic Resonance Angiography Using Landmark Subsets
          </a>
        </h4>
      
        <p class="journal-authors">
          Yura Jeong, Daehyun Kwon,
          <strong>Se-On Kim</strong>,
          Ga-Hyeon Kim, Min-Seo Park, Yoon-Chul Kim
        </p>
      
        <p class="journal-name">
          Investigative Magnetic Resonance Imaging, 2026 Mar
        </p>
      
      </article>

    </div>

  </section>

  <!-- Domestic Journal -->
  <section class="journal-section" id="domestic">

    <div class="journal-section-header">
      <h2>Domestic Journal</h2>
      <span>0 Papers</span>
    </div>

    <p class="journal-empty">
      No publications yet.
    </p>

  </section>

  <p id="journal-no-results" hidden>
    No matching publications found.
  </p>

</section>

<!-- Publication Search -->
<script>
document.addEventListener("DOMContentLoaded", function () {

  const search = document.getElementById("journal-search");
  const papers = document.querySelectorAll(".journal-paper");
  const groups = document.querySelectorAll(".journal-year-group");
  const noResults = document.getElementById("journal-no-results");

  search.addEventListener("input", function () {

    const keyword = search.value.toLowerCase().trim();
    let visibleCount = 0;

    papers.forEach(function (paper) {

      const text = paper.textContent.toLowerCase();
      const matched = text.includes(keyword);

      paper.hidden = !matched;

      if (matched) visibleCount++;

    });

    groups.forEach(function (group) {

      const visiblePapers =
        group.querySelectorAll(".journal-paper:not([hidden])");

      group.hidden = visiblePapers.length === 0;

    });

    noResults.hidden = visibleCount !== 0;

  });

});
</script>
