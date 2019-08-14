# e2dubba.github.io

[The Political Theology Topic Model visualisation is available here](politicotheological.html)

## Bibliography

[A Bibliography is available here](bibliography.html)

## List of Blog posts 

<ul>
    {% for post in site.posts %}
    <li>
    <a href="{{ post.url }}">{{post.date | date: "%A, %b %-d, %Y" }}: {{ post.title }} </a>
    </li>
    {% endfor %}
</ul>
