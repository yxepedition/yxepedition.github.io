---
layout: page
title: Archives
---

{% capture site_tags %}{% for tag in site.tags %}{{tag | first}}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
{% assign sortedTags=site_tags | split:',' | sort %}

<ul class="tag-cloud">
{% for tag in sortedTags %}
<li><a href="#{{tag | cgi_escape}}"><code class="highligher-rouge"><nobr>{{tag}} [{{site.tags[tag].size}}] </nobr></code>&nbsp;</a></li>
{% endfor %}
</ul>

<article class="archive">
{% for tag in sortedTags %}
  <h3 id="{{tag | cgi_escape}}"><code class="highligher-rouge">{{tag}}</code></h3>
  <ul class="taglist">
    {% for post in site.tags[tag] %}
    <li>
          <time itemprop="dateCreated" datetime="{{post.date}}">
                {{ post.date | date: "%b %d, %Y" }}</time> | <a href="{{site.baseurl}}{{post.url}}" rel="bookmark" title="Permanent Link to {{site.baseurl}}{{post.url}}">
                {{post.title}}</a>
    </li>
    {% endfor %}
    <li class="return"><a href="#top" title="return to top">return to top</a></li>
  </ul>
  {% endfor %}
  </article>