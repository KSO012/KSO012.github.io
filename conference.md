---
layout: default
title: Conference
nav: conference
permalink: /conference/
---

<section class="page-intro">
  <div class="eyebrow">PUBLICATIONS</div>
  <h1>Conference</h1>
  <p>Conference papers and presentations.</p>
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

    <!-- Add international papers here -->

    <p class="journal-empty">
      Conference papers will be listed here.
    </p>

  </section>

  <!-- Domestic Conference -->
  <section class="journal-section" id="domestic">

    <div class="journal-section-header">
      <h2>Domestic Conference</h2>
      <span>0 Papers</span>
    </div>

    <!-- Add domestic papers here -->

    <p class="journal-empty">
      Conference papers will be listed here.
    </p>

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
