---
layout: page
permalink: /students/
title: students
description: 
nav: true
nav_order: 3
pretty_table: true
---

## Alumni

<hr>

<style>
  .alumni-toggle {
    display: flex;
    gap: 0.5rem;
    margin-bottom: 1.25rem;
  }
  .alumni-toggle-btn {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.5rem 1.1rem;
    border-radius: 999px;
    border: 1px solid var(--global-divider-color, #ddd);
    background: transparent;
    color: inherit;
    cursor: pointer;
    font-size: 0.95rem;
    transition: background 0.15s ease, color 0.15s ease, border-color 0.15s ease;
  }
  .alumni-toggle-btn.active {
    background: var(--global-theme-color, #375eab);
    border-color: var(--global-theme-color, #375eab);
    color: #fff;
  }
  .alumni-count-badge {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    min-width: 1.6rem;
    height: 1.4rem;
    padding: 0 0.4rem;
    border-radius: 999px;
    background: rgba(127, 127, 127, 0.18);
    font-size: 0.8rem;
    font-weight: 600;
  }
  .alumni-toggle-btn.active .alumni-count-badge {
    background: rgba(255, 255, 255, 0.25);
  }
  .alumni-panel {
    display: none;
  }
  .alumni-panel.active {
    display: block;
  }
  .alumni-table-wrap {
    border: 1px solid var(--global-divider-color, #e5e5e5);
    border-radius: 0.6rem;
    overflow: hidden;
  }
  .alumni-table-wrap .fixed-table-toolbar {
    padding: 0.6rem 0.75rem;
  }
  .alumni-table-wrap table th {
    position: sticky;
    top: 0;
  }
  .alumni-table-wrap table tbody tr:hover {
    background: rgba(127, 127, 127, 0.08);
  }
</style>

<div class="alumni-toggle" role="tablist">
  <button type="button" class="alumni-toggle-btn active" data-target="pregrado" role="tab" aria-selected="true">
    <i class="fa-solid fa-user-graduate"></i>
    Pregrado
    <span class="alumni-count-badge" id="graduated-count">23</span>
  </button>
  <button type="button" class="alumni-toggle-btn" data-target="postgrado" role="tab" aria-selected="false">
    <i class="fa-solid fa-graduation-cap"></i>
    Postgrado
    <span class="alumni-count-badge" id="postgraduated-count">23</span>
  </button>
</div>

<div class="alumni-panel active" id="panel-pregrado">
  <div class="alumni-table-wrap">
    <table
      id="graduated-table"
      data-click-to-select="false"
      data-height="520"
      data-pagination="true"
      data-page-size="10"
      data-page-list="[10, 25, 50, All]"
      data-search="true"
      data-sort-name="year"
      data-sort-order="desc"
      data-striped="true"
      data-toggle="table"
      data-url="{{ '/assets/json/table_graduated.json' | relative_url }}"
    >
      <thead>
        <tr>
          <th data-field="year" data-halign="left" data-align="center" data-sortable="true">year</th>
          <th data-field="name" data-halign="left" data-align="left" data-sortable="false">names</th>
          <th data-field="title" data-halign="left" data-align="left" data-sortable="false">title</th>
          <th data-field="program" data-halign="left" data-align="left" data-sortable="true">program</th>
          <th data-field="university" data-halign="left" data-align="left" data-sortable="true">university</th>
        </tr>
      </thead>
    </table>
  </div>
</div>

<div class="alumni-panel" id="panel-postgrado">
  <div class="alumni-table-wrap">
    <table
      id="postgraduated-table"
      data-click-to-select="false"
      data-height="520"
      data-pagination="true"
      data-page-size="10"
      data-page-list="[10, 25, 50, All]"
      data-search="true"
      data-sort-name="year"
      data-sort-order="desc"
      data-striped="true"
      data-toggle="table"
      data-url="{{ '/assets/json/table_postgraduated.json' | relative_url }}"
    >
      <thead>
        <tr>
          <th data-field="year" data-halign="left" data-align="center" data-sortable="true">year</th>
          <th data-field="name" data-halign="left" data-align="left" data-sortable="false">names</th>
          <th data-field="title" data-halign="left" data-align="left" data-sortable="false">title</th>
          <th data-field="program" data-halign="left" data-align="left" data-sortable="true">program</th>
          <th data-field="university" data-halign="left" data-align="left" data-sortable="true">university</th>
        </tr>
      </thead>
    </table>
  </div>
</div>

<script>
  (function () {
    // Toggle entre Pregrado / Postgrado
    var buttons = document.querySelectorAll('.alumni-toggle-btn');
    buttons.forEach(function (btn) {
      btn.addEventListener('click', function () {
        buttons.forEach(function (b) {
          b.classList.remove('active');
          b.setAttribute('aria-selected', 'false');
        });
        btn.classList.add('active');
        btn.setAttribute('aria-selected', 'true');

        document.querySelectorAll('.alumni-panel').forEach(function (p) {
          p.classList.remove('active');
        });
        document.getElementById('panel-' + btn.dataset.target).classList.add('active');
      });
    });

    // Conteo dinámico: se actualiza con la cantidad real de filas cargadas desde cada JSON
    function bindCount(tableId, countId) {
      if (!window.jQuery) return;
      jQuery('#' + tableId).on('load-success.bs.table', function (e, data) {
        document.getElementById(countId).textContent = Array.isArray(data) ? data.length : (data.total || data.length);
      });
    }
    bindCount('graduated-table', 'graduated-count');
    bindCount('postgraduated-table', 'postgraduated-count');
  })();
</script>
