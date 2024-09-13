# Welcome to my blog :)

## About me

Hello, my name is nahid. I attend Brooklyn STEAM Center. I am currently learning Full-Stack Development.
 
 [Personal Website](https://unhabit.github.io)

 ## Recent Posts

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>