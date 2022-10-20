---
title: Menulis Konten dengan Nuxt Content
img: https://images.unsplash.com/reserve/LJIZlzHgQ7WPSh5KVTCB_Typewriter.jpg?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=60
description: Langkah-langkah menulis dengan Nuxt Content
author:
  name: Agung Hidayat
---

# Menulis Konten dengan Nuxt Content

Pada dasarnya nuxt content memiliki pengaturaan bawaan untuk memparsing file `.md` dan `.yaml` yang beraada dalam sebuah folder bernama `content` [^1]

```
├── content
│   └── YOUR CONTENT.md
├── pages
├── static
└── store
```

Didalam file markdown kita dapat menyisipkan tag html dan juga component dari vue
<!-- Tag HTML -->
<h3>
  Ini Tag html
</h3>

<!-- Vue Component -->
<Tips>
  Ini adalah Sebuah Tips
</Tips>

## Catatan Kaki
[^1]:[Nuxt Content Writing Content](https://content.nuxtjs.org/guide/writing/content-directory#content-directory)
