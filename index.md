## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/porolakka/0x0026/edit/master/index.md) to maintain and preview the content for your website in Markdown files.



---

<h3>最新記事</h3>

<ul>
  {% for post in site.posts limit 5 %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>


<h3>カテゴリー</h3>
  
{% for category in site.categories %}
  {% capture name %}{{ category[0] }}{% endcapture %}
  <h2>{{ name }} ({{ site.categories[name] | size }})</h2>
  <ul class="posts">
  {% for post in site.categories[name] %}
    <li>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      <span class="post-date">{{ post.date | date_to_string }}</span>
    </li>
  {% endfor %}
  </ul>
{% endfor %}
