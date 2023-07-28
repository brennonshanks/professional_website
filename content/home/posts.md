---
widget: collection
widget_id: post
headless: true
weight: 20
title: Posts
active: true
content:
  # Page type to display. E.g. post, event, publication...
  page_type: post
  # Choose how many pages you would like to display (0 = all pages)
  count: 5
  # Filter on criteria
  filters:
    author: ''
    category: ''
    tag: ''
    exclude_featured: false
    exclude_future: false
    exclude_past: false
    publication_type: ''
  filter_button:
    - name: All
      tag: '*'
    - name: Thermodynamics
      tag: thermodynamics
    - name: Statistical Mechanics
      tag: statistical mechanics
    - name: Quantum Mechanics
      tag: quantum mechanics
    - name: Machine Learning
      tag: machine learning

  # Choose how many pages you would like to offset by
  offset: 0
  # Page order: descending (desc) or ascending (asc) date.
  order: desc
design:
  columns: "2"
  background:
    text_color_light: false
    image_darken: 0
---
