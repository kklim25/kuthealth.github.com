---
layout: page
title: Jekyll 테스트 블로그입니다.
---
{% include JB/setup %}

<ul>
{% for post in paginator.posts %}
  <li>
    <a href="{{ BASE_PATH }}{{ post.url }}"><span>{{ post.title }}</span></a>
    <span>{{ post.date | date: "%Y-%m-%d" }}</span>
    <p>{{ post.content | truncate: 15 }}</p>
    <p><a class="btn js-btn" href="{{ BASE_PATH }}{{ post.url }}">더 보기 &raquo;</a></p>
  </li>
{% endfor %}
</ul>

<div class="pagination">
  <ul>
{% if paginator.previous_page %}
    <li>
  {% if paginator.previous_page == 1 %}
      <a href="{{ BASE_PATH }}/">&laquo;</a>
  {% else %}
      <a href="{{ BASE_PATH }}/page{{paginator.previous_page}}">&laquo;</a>
  {% endif %}
    </li>
{% else %}
    <li class="disabled">
      <a href="#">&laquo;</a>
    </li>
{% endif %}

{% if paginator.page == 1 %}
    <li class="active">
      <a href="#">1</a>
    </li>
{% else %}
    <li>
      <a href="{{ BASE_PATH }}/">1</a>
    </li>
{% endif %}

{% for count in (2..paginator.total_pages) %}
  {% if count == paginator.page %}
    <li class="active">
      <a href="#">{{count}}</a>
    </li>
  {% else %}
    <li>
      <a href="{{ BASE_PATH }}/page{{count}}">{{count}}</a>
    </li>
  {% endif %}
{% endfor %}

{% if paginator.next_page %}
    <li>
      <a href="{{ BASE_PATH }}/page{{paginator.next_page}}">&raquo;</a>
    </li>
{% else %}
    <li class="disabled">
      <a href="#">&raquo;</a>
    </li>
{% endif %}
  </ul>
</div>
