---
layout: default
title: Conference
nav: conference
permalink: /conference/
---

<section class="page-intro">
  <div class="eyebrow">PUBLICATION</div>
  <h1>Conference</h1>
</section>

<div class="journal-page conference-page">

  <!-- Publication Statistics -->
  <div class="journal-stats">

    <div class="journal-stat">
      <strong>00</strong>
      <span>Conference Papers</span>
    </div>

    <a href="#international"
       class="journal-stat journal-stat-link">
      <strong>00</strong>
      <span>International Conference Papers</span>
    </a>

    <a href="#domestic"
       class="journal-stat journal-stat-link">
      <strong>00</strong>
      <span>Domestic Conference Papers</span>
    </a>

  </div>

  <!-- Search -->
  <div class="journal-search">
    <input
      type="search"
      id="journal-search"
      placeholder="Search by title, author, or conference..."
      aria-label="Search conference papers"
    >
  </div>

  <!-- International Conference -->
  <section class="journal-section" id="international">
  
    <div class="journal-section-header">
      <h2>International Conference</h2>
      <span>0 Papers</span>
    </div>
  
    <!-- 2026 -->
  
    <div class="journal-year-group">
  
      <h3 class="journal-year">2026</h3>
  
      <!-- EMNLP 2026 -->
      <article class="journal-paper">
  
        <div class="journal-badges">
          <span>Conference</span>
          <span>International</span>
        </div>
  
        <h4>
          Uncertainty Meets Conformance: A Process Mining-based Multi-Objective Evaluation for Clinical Reasoning using LLMs
        </h4>
  
        <p class="journal-authors">
          <strong>Seon Kim</strong>, Jeong-woo Lee, Tae Hoon Kong*, Jongchan Kim*
        </p>
  
        <p class="journal-name">
          Third Workshop on Uncertainty-Aware NLP (UncertaiNLP), 2026 Conference on Empirical Methods in Natural Language Processing (EMNLP 2026), Budapest, Hungary
        </p>
  
      </article>
  
      <!-- ASPAI 2026 -->
      <article class="journal-paper">
  
        <div class="journal-badges">
          <span>Conference</span>
          <span>International</span>
        </div>
  
        <h4>
          A comparative analysis of trace encoding methods for next activity predictive process monitoring
        </h4>
  
        <p class="journal-authors">
          <strong>Seon Kim</strong>, Chaeyeon Park, Youngwoo Ko, Hyunwoo Jo, Jongchan Kim*
        </p>
  
        <p class="journal-name">
          2nd Asia-Pacific Symposium on Process and AI (ASPAI 2026), Pohang, Republic of Korea
        </p>
  
      </article>
  
    </div>
  
    <!-- 2025 -->
  
    <div class="journal-year-group">
  
      <h3 class="journal-year">2025</h3>
  
      <!-- ICPM 2025 -->
      <article class="journal-paper">
  
        <div class="journal-badges">
          <span>Conference</span>
          <span>International</span>
        </div>

        <h4>
          <a href="https://icpmconference.org/2025/proceedings/"
             target="_blank"
             rel="noopener noreferrer">
            Bus stop congestion monitoring based on process discovery algorithms
          </a>
        </h4>
        
        <p class="journal-authors">
          <strong>Seon Kim</strong>, Jungtak Oh,
          Jongchan Kim*
        </p>
  
        <p class="journal-name">
          Empirical Research in Process Mining Workshop (ERPM), 7th International Conference on Process Mining (ICPM 2025), Montevideo, Uruguay
        </p>
  
      </article>
  
    </div>
  
  </section>

  <!-- Domestic Conference -->
  <section class="journal-section" id="domestic">
  
    <div class="journal-section-header">
      <h2>Domestic Conference</h2>
      <span>0 Papers</span>
    </div>
  
    <!-- 2025 -->
  
    <div class="journal-year-group">
  
      <h3 class="journal-year">2025</h3>
  
      <article class="journal-paper">
  
        <div class="journal-badges">
          <span>Conference</span>
          <span>Domestic</span>
        </div>
  
        <h4>
          프로세스 디스커버리 알고리즘 기반 버스정류장 혼잡도 모니터링
        </h4>
  
        <p class="journal-authors">
          <strong>김세온</strong>, 김종찬*
        </p>
  
        <p class="journal-name">
          2025 한국인공지능융합기술학회 춘계학술대회
        </p>
  
      </article>
  
    </div>
  
  </section>

  <p id="conference-no-results" hidden>
    No matching conference papers found.
  </p>

</div>

<!-- Conference Functions -->
<script>
document.addEventListener("DOMContentLoaded", function () {

  const page = document.querySelector(".conference-page");

  if (!page) return;

  const internationalSection =
    page.querySelector("#international");

  const domesticSection =
    page.querySelector("#domestic");

  // 1. Count conference papers
  const international = internationalSection.querySelectorAll(
    ".journal-paper"
  ).length;

  const domestic = domesticSection.querySelectorAll(
    ".journal-paper"
  ).length;

  const total = international + domestic;

  // 2. Update statistics
  const stats = page.querySelectorAll(
    ".journal-stats .journal-stat"
  );

  const counts = [total, international, domestic];

  stats.forEach(function (stat, index) {
    const number = stat.querySelector("strong");

    if (number) {
      number.textContent =
        String(counts[index]).padStart(2, "0");
    }
  });

  // 3. Update statistics labels
  if (stats.length >= 3) {
    stats[0].querySelector("span").textContent =
      "Conference " + (total === 1 ? "Paper" : "Papers");

    stats[1].querySelector("span").textContent =
      "International Conference " +
      (international === 1 ? "Paper" : "Papers");

    stats[2].querySelector("span").textContent =
      "Domestic Conference " +
      (domestic === 1 ? "Paper" : "Papers");
  }

  // 4. Update section counts
  [
    [internationalSection, international],
    [domesticSection, domestic]
  ].forEach(function (item) {

    const section = item[0];
    const count = item[1];

    const label = section.querySelector(
      ".journal-section-header > span"
    );

    if (label) {
      label.textContent =
        count + (count === 1 ? " Paper" : " Papers");
    }

    const empty = section.querySelector(".journal-empty");

    if (empty) {
      empty.hidden = count > 0;
    }

  });

  // 5. Search conference papers
  const search = page.querySelector("#journal-search");

  const papers = page.querySelectorAll(".journal-paper");

  const groups = page.querySelectorAll(
    ".journal-year-group"
  );

  const noResults = page.querySelector(
    "#conference-no-results"
  );

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

      const visible = group.querySelectorAll(
        ".journal-paper:not([hidden])"
      );

      group.hidden = visible.length === 0;

    });

    noResults.hidden =
      keyword === "" || visibleCount > 0;

  });

});
</script>
