---
layout: page
title: LecturesByTag
desc: "UVa CS 4501 Machine Learning Lectures Organized by Tags"
---
<p><a name="topPage"></a></p>


Click on a tag to see relevant list of lectures.

<ul class="tags">
{% assign sorted = site.tags | sort %}
{% for tag in sorted %}
  {% assign t = tag | first %}
  <li><a href="{{ site.baseurl }}/LecturesByTags/#{{t | replace:" ","-" }}">{{ t }}</a></li>
{% endfor %}
</ul>

---

{% assign sorted = site.tags | sort %}
{% for tag in sorted %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

<h1><a name="{{t | replace:" ","-" }}"></a><a class="internal" href="{{ site.baseurl }}/LecturesByTags/#{{t | replace:" ","-" }}">{{ t  }}</a></h1>

<!--- for each tag, get a table of index -->

<table id="datatab3" summary="Table of Lectures" border="1">
<tr>
 <h3><b>
  <th>No.</th>
  <th>Date</th>
  <th>Week</th>
  <th>Title</th>
  <th>Lecture</th>
  <th>Lecture <br>Version</th>
  <th>Extra <br>Content</th>
  <th>Notes</th>
  </b>
  </h3>
</tr>


{% assign counter = 1 %}
{% assign sortedp = posts  | sort: 'date' %}

{% for post in sortedp %}
  {% if post.tags contains t %}

  <tr>
  <td>{{ counter }}</td>
  <td><span class="date"> {{ post.date | date: "%-b, %-d "  }}</span></td>
  <td>{{ post.desc }}</td>
  <!---<td><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }} </a></td> -->


  {% if t contains "0Logistics" %}
  <td><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }} </a></td>
  {% else %}
  <td>{{ post.title }}</td>
  {% endif %}

  {% if post.lecture %}
  <td><a href="{{ site.baseurl }}/Lectures/{{ post.lecture }}.pdf">Slide</a></td>
  <td>{{ post.lectureVersion }}</td>
  {% else %}
  <td></td>
  <td></td>
  {% endif %}


  {% if post.extraContent %}
  <td><a href="{{ site.baseurl }}/Lectures/{{ post.extraContent }}.pdf"> PDF </a></td>
  {% else %}
  <td></td>
  {% endif %}

  <td>{{ post.notes }} </td>
  </tr>

  {% assign counter=counter | plus:1 %}
  {% endif %}
{% endfor %}
</table>

<!--- for each tag, present its posts in orders -->


{% endfor %}


<div style="position: fixed; bottom: 76px; right:10px; width: 88px; height: 36px; background-color: #FFCF79;">
<a style="position: fixed; bottom:80px; right:10px;" href="#topPage" title="Back to Top">BackTop</a>
</div>
