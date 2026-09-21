---
Title: "{{title | escape}}"
Year: {% if date and date.format %}{{date | format("YYYY")}}{% else %}n.d.{% endif %}
Authors: {% if authors %}{{authors}}{% else %}Unknown{% endif %}
Tags: [{% for t in tags %}{{t.tag.split(" ").join("_")}}{% if not loop.last %}, {% endif %}{% endfor %}]
---
Zotero PDF Link: {{pdfZoteroLink}}
Related: {% for relation in relations | selectattr("citekey") %} [[{{relation.citekey}}]]{% if not loop.last %}, {% endif%} {% endfor %}

### Persistent Notes
{% persist "notes" %}{% if isFirstImport %}
{% endif %}
{% endpersist %}

### In-text annotations

{% for annotation in annotations -%}
{%- if annotation.annotatedText -%}
{% if annotation.color %} <mark class="hltr-{{annotation.colorCategory | lower}}">"{{annotation.annotatedText | safe}}"</mark> {% else %} {{annotation.type | capitalize}} {% endif %}[Page {{annotation.pageLabel}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}})
{%- endif %}
{% if annotation.comment %}
{{annotation.comment | safe}} [Page {{annotation.pageLabel}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}})
{% endif %}
{% if annotation.allTags %}
{{annotation.allTags}}
{% endif %}
{% endfor -%}