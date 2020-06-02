# e2dubba.github.io

## Projects

- [The Political Theology Topic Model visualisation is available here](politicotheological.html)

- [Linked-Amarna: A Graph approach to Personal names in the Amarna
  Letters](http://e2dubba.github.io/linked-amarna)


## List of Blog posts 

<ul>
    {% for post in site.posts %}
    <li>
    <a href="{{ post.url }}">{{post.date | date: "%A, %b %-d, %Y" }}: {{ post.title }} </a>
    </li>
    {% endfor %}
</ul>
