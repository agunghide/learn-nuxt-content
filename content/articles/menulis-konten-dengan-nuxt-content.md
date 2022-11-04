---
title: Menulis Konten dengan Nuxt Content
img: https://images.unsplash.com/reserve/LJIZlzHgQ7WPSh5KVTCB_Typewriter.jpg?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=60
description: Langkah-langkah menulis dengan Nuxt Content
author:
  name: Agung Hidayat
---

# Menulis Konten dengan Nuxt Content

Pada dasarnya nuxt content memiliki pengaturaan bawaan untuk memparsing file `.md` dan `.yaml` yang berada dalam sebuah folder bernama `content` [^1]

```bash
├── content
│   └── YOUR CONTENT.md
├── pages
├── static
└── store
```
---
# Heading 1
This is some more info

## Heading 2
This is some more info  

### Heading 3
This is some more info 

#### Heading 4
This is some more info 

---
## Emphasis

**Bold text**  
*Italic Text*  
***Bold and Italic Text***  

---

## Blockquote

> Kiri kanan kulihat saja, banyak pohon cemara aaaa.

---

## List

### Ordered List
1. First item
2. Second item
3. Third item
4. Fourth item

### Unordered List
- First item
- Second item
- Third item
- Fourth item

---
## Image

![The San Juan Mountains are beautiful!](https://images.unsplash.com/photo-1533636721434-0e2d61030955?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2550&q=80 "San Juan Mountains")

---

## Table

| Headings | Description |
|----------|-------------|
| H1 | Ini H1 |
| H2 | Ini H2 |

---


Didalam file markdown kita dapat menyisipkan tag html dan juga component dari vue

<!-- Tag Html-->
<h3>
  Yang ini Tag html
</h3>


<!-- Component Vue dengan passing props -->
<tips 
  type="primary" 
  icon="💡" 
  text="Kalau yang ini adalah komponen Vue">
</tips>


<!-- Component Vue dengan slot -->

<br />

## Catatan Kaki
[^1]:[Nuxt Content Writing Content](https://content.nuxtjs.org/guide/writing/content-directory#content-directory)
