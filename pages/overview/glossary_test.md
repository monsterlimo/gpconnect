---
title: Glossary
keywords: abbreviations, definitions, glossaries, terms
tags: [getting_started]
sidebar: overview_sidebar
permalink: glossary_test.html
summary: "Glossary of terms used in the GP Connect specification"
toc: false
---

Example data like: https://gist.github.com/ThoMo/fb3cb24dc8d14a53af97

<table>
<thead><tr><th>Term</th><th>Description</th></tr></thead>
<tbody>
{% assign gs = site.data.glossary | sort:[0] %}
{% for kv in gs %}
<tr> <td>{{ kv[0] }} </td><td> {{ kv[1] }} </td></tr>
{% endfor %}
</tbody>
