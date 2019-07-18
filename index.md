## Home

0x0026 = & 

世の中に溢れている可能性のひとつひとつ

やってみた、つくってみた、つかってみた

ちょっとずつ記録する場所

---

<h2>記事一覧</h2>

<h3>新着</h3>

<ul>
  {% for post in site.posts limit 5 %}
    <li>
      <a href="{{ post.url  | prepend: site.baseurl}}">{{ post.title }}</a>
      <span class="post-date">{{ post.date | date_to_string }}</span>
    </li>
  {% endfor %}
</ul>


<h3>カテゴリー</h3>
  
{% for category in site.categories %}
  {% capture name %}{{ category[0] }}{% endcapture %}
  <h4>{{ name }} ({{ site.categories[name] | size }})</h4>
  <ul class="posts">
  {% for post in site.categories[name] %}
    <li>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      <span class="post-date">{{ post.date | date_to_string }}</span>
    </li>
  {% endfor %}
  </ul>
{% endfor %}

<h3>タグ</h3>

{% for tag in site.tags %}
  {% capture name %}{{ tag[0] }}{% endcapture %}
  <h4>{{ name }} ({{ site.tags[name] | size }})</h4>
  <ul class="posts">
  {% for post in site.tags[name] %}
    <li>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      <span class="post-date">{{ post.date | date_to_string }}</span>
    </li>
  {% endfor %}
  </ul>
{% endfor %}
