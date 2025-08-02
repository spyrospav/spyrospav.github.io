---

layout: pubs
title: Publications
content_class: custom-content

---

*<sup>\*</sup>Denotes equal contribution.*

{% assign publications_by_year = site.data.publications | group_by: "year" | sort: "name", "last" | reverse %}

{% for year_group in publications_by_year %}
### {{ year_group.name }}

<ul>
{% for pub in year_group.items %}
  <li>
    <strong>{{ pub.title }}</strong><br>
    {% for author_id in pub.authors %}
      {%- assign author = site.data.authors[author_id] -%}
      {%- if author_id == 'spyros_pavlatos' -%}
        <strong>{{ author.name }}</strong>
      {%- else -%}
        <a href="{{ author.url }}">{{ author.name }}</a>
      {%- endif -%}
      {%- if pub.equal_contribution contains author_id -%}<sup>*</sup>{%- endif -%}
      {%- unless forloop.last -%}, {% endunless %}
    {%- endfor -%}.<br>
    <em>{{ pub.conference }}</em>
    {% if pub.links.size > 0 %}
      <br>
      {% for link in pub.links %}
        [<a href="{{ link.url }}">{{ link.name }}</a>]
      {% endfor %}
    {% endif %}
  </li>
{% endfor %}
</ul>
{:.larger}
{% endfor %}