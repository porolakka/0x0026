## 概要

0x0026 = & 

世の中に溢れている可能性のひとつひとつ

やってみた、つくってみた、つかってみた

ちょっとずつ記録する場所

---

<h2>新着記事</h2>

<ul>
  {% for post in site.posts limit 5 %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>


<h2>カテゴリー</h2>
  
{% for category in site.categories %}
  {% capture name %}{{ category[0] }}{% endcapture %}
  <h3>{{ name }} ({{ site.categories[name] | size }})</h3>
  <ul class="posts">
  {% for post in site.categories[name] %}
    <li>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      <span class="post-date">{{ post.date | date_to_string }}</span>
    </li>
  {% endfor %}
  </ul>
{% endfor %}
