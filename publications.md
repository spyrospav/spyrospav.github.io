---

layout: pubs
title: Publications
content_class: custom-content

---

*<sup>\*</sup>Denotes equal contribution.*

{% assign under_submission = site.data.publications | where: "status", "under_submission" %}
{% assign published = site.data.publications | where_exp: "pub", "pub.status == nil" %}

{% if under_submission.size > 0 %}
### Under Submission

<ul>
{% for pub in under_submission %}
  {% include publication.html pub=pub %}
{% endfor %}
</ul>
{:.larger}
{% endif %}

{% assign publications_by_year = published | group_by: "year" | sort: "name", "last" | reverse %}

{% for year_group in publications_by_year %}
### {{ year_group.name }}

<ul>
{% for pub in year_group.items %}
  {% include publication.html pub=pub %}
{% endfor %}
</ul>
{:.larger}
{% endfor %}
