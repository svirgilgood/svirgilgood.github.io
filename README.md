# e2dubba.github.io

[The Political Theology Topic Model visualisation is available here](politicotheological.html)

## List of Blog posts 

<ul>
    {% for post in site.posts %}
    <li>
    <a href="{{ post.url }}">{{ post.title }} </a>
    </li>
    {% endfor %}
</ul>
