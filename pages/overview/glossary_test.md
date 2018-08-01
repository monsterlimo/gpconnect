---
title: Glossary
keywords: abbreviations, definitions, glossaries, terms
tags: [getting_started]
sidebar: overview_sidebar
permalink: glossary_test.html
summary: "Glossary of terms used in the GP Connect specification"
toc: false
---

<table>
<thead><tr><th>Term</th><th>Description</th></tr></thead>
<tbody>
{% assign gs = site.data.glossary | sort:[0] %}
{% for kv in gs %}
<tr> <td>{{ kv[0] }} </td><td> {{ kv[1] }} </td></tr>
{% endfor %}
</tbody>


{% assign glossaryTerms = site.data.glossary %}

{% for entry in glossaryTerms %}
{{entry.term}}
{{entry.def}}
{% endfor %}
