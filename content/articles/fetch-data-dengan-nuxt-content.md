---
title: Fetch data dengan Nuxt Content
img: https://images.unsplash.com/photo-1588065394015-68bf7e40738d?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=634&q=80
description: Langkah-langkah menulis dengan Nuxt Content
author:
  name: Agung Hidayat
---

# Fetch data dengan Nuxt Content

Modul ini membuat instance **`$content`** secara global, artinya kita dapat mengaksesnya di mana saja menggunakan **`this.$content`**.  
Untuk plugin, asyncData, nuxtServerInit dan Middleware, kita dapat mengaksesnya dari **`context.$content`**. [^1]

Contoh untuk mengambil sebuah konten dengan menggunakan method **`$content`** adalah sebgai berikut
```
async asyncData ({ $content, params }) {
   const content = await $content(params.slug).fetch()
}
```
Kita juga dapat memberikan beberapa argumen
```
$content('articles', params.slug)
```
yang akan diterjemahkan ke **`/articles/${params.slug}`**



## Catatan Kaki
[^1]:[Nuxt Content Fetching Content](https://content.nuxtjs.org/v1/getting-started/fetching)
