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

<table class="table table-sm table-hover" id="students-table">
  <thead>
    <tr>
      <th scope="col">Year</th>
      <th scope="col">Names</th>
      <th scope="col">Title</th>
      <th scope="col">Program</th>
      <th scope="col">University</th>
    </tr>
  </thead>
  <tbody id="students-tbody">
    <tr><td colspan="5" class="text-center text-muted">Loading...</td></tr>
  </tbody>
</table>

<br>

<script>
  fetch('{{ "/assets/json/table_students.json" | relative_url }}')
    .then(response => response.json())
    .then(data => {
      const tbody = document.getElementById('students-tbody');
      tbody.innerHTML = '';

      data.forEach(student => {
        const row = document.createElement('tr');
        row.innerHTML = `
          <td>${student.year ?? ''}</td>
          <td>${student.name ?? ''}</td>
          <td>${student.title ?? ''}</td>
          <td>${student.program ?? ''}</td>
          <td>${student.university ?? ''}</td>
        `;
        tbody.appendChild(row);
      });
    })
    .catch(() => {
      document.getElementById('students-tbody').innerHTML =
        '<tr><td colspan="5" class="text-center text-danger">Error loading data.</td></tr>';
    });
</script>