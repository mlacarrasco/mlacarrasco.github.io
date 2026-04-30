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

<table class="table table-sm table-hover">
  <thead>
    <tr>
      <th scope="col">Year</th>
      <th scope="col">Names</th>
      <th scope="col">Title</th>
      <th scope="col">Program</th>
      <th scope="col">University</th>
    </tr>
  </thead>
  <tbody>
    {% for student in site.data.table_students %}
    <tr>
      <td>{{ student.year }}</td>
      <td>{{ student.name }}</td>
      <td>{{ student.title }}</td>
      <td>{{ student.program }}</td>
      <td>{{ student.university }}</td>
    </tr>
    {% endfor %}
  </tbody>
</table>
