---
layout: default
title: People
---

<!-- Principal Investigator Section -->
### Principal Investigator

{% for person in site.data.people.pi %}
<div class="person-card">
  <img src="{{ person.photo | relative_url }}" alt="{{ person.name }}">
  <div class="person-info">
    <h4>{{ person.name }}</h4>
    <span class="role">{{ person.role }}</span>
    <p>{{ person.description }}</p>
  </div>
</div>
{% endfor %}

<!-- Postdoctoral Researchers Section -->
### Postdoctoral Researchers

{% for person in site.data.people.postdocs %}
<div class="person-card">
  <img src="{{ person.photo | relative_url }}" alt="{{ person.name }}">
  <div class="person-info">
    <h4>{{ person.name }}</h4>
    <span class="role">{{ person.role }}</span>
    <p>{{ person.description }}</p>
  </div>
</div>
{% endfor %}

<!-- PhD Students Section -->
### PhD Students

{% for person in site.data.people.phd_students %}
<div class="person-card">
  <img src="{{ person.photo | relative_url }}" alt="{{ person.name }}">
  <div class="person-info">
    <h4>{{ person.name }}</h4>
    <span class="role">{{ person.role }}</span>
    <p>{{ person.description }}</p>
  </div>
</div>
{% endfor %}

<!-- Student Assistants Section -->
### Student Assistants

{% for person in site.data.people.assistants %}
<div class="person-card">
  <img src="{{ person.photo | relative_url }}" alt="{{ person.name }}">
  <div class="person-info">
    <h4>{{ person.name }}</h4>
    <span class="role">{{ person.role }}</span>
    <p>{{ person.description }}</p>
  </div>
</div>
{% endfor %}
