---
author: someone
layout: post-full
type: gallery
featimg: gallery-2.jpg
title: Galeria de Imagens
tags: [gallery, image]
category: [image]
gallery:
    - images:
      - filename: gallery-1.jpg
        alttext: Bloom Flat
      - filename: gallery-2.jpg
        alttext: Bloom
      - filename: gallery-3.jpg
        alttext: Blossom in a Star
      - filename: gallery-4.jpg
        alttext: Blossom
      - filename: gallery-5.jpg
        alttext: Bubbly Bloom
      - filename: gallery-6.jpg
        alttext: Rays of Gold
      - filename: gallery-7.jpg
        alttext: Exotic
      - filename: gallery-8.jpg
        alttext: Filled out
---

Nullam blandit bibendum augue a hendrerit. Morbi vulputate nibh et erat scelerisque, eu imperdiet nisi commodo. In nunc turpis, sollicitudin eget ultricies non, ultrices iaculis nulla. Aliquam facilisis, lorem sed mattis fermentum, magna purus placerat neque, at auctor enim odio a orci. Nullam interdum purus orci, sit amet posuere lacus sagittis quis. Nunc sed turpis aliquet, ultricies orci et, venenatis tellus. Duis egestas tempus tellus in tempor. Mauris ac quam efficitur massa dignissim tincidunt.

Galleries are defined in a data-sheet, set type and gallery-id in front matter and include `gallery_lightbox.html` within the content.
<br>

###### front matter

```yml
---
layout: post-full
type: gallery
gallery:
    - images:
      - filename: gallery-1.jpg
        alttext: Bloom Flat
      - filename: gallery-2.jpg
        alttext: Bloom
      - filename: gallery-3.jpg
        alttext: Blossom in a Star
      - filename: gallery-4.jpg
        alttext: Blossom
      - filename: gallery-5.jpg
        alttext: Bubbly Bloom
      - filename: gallery-6.jpg
        alttext: Rays of Gold
      - filename: gallery-7.jpg
        alttext: Exotic
      - filename: gallery-8.jpg
        alttext: Filled out
---
```
<br>

###### post content

``` liquid
{% raw  %}
{% include gallery_lightbox.html %}
{% endraw %}
```

{% include gallery_lightbox.html %}