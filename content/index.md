<!-- Menampilkan tag html -->
<div class="p-4 mb-4 text-white bg-blue-500">
  This is HTML inside markdown that has a class of note
</div>

<!-- Menampilkan komponen -->
<info-box>
  <template #info-box>
    This is a vue component inside markdown using slots
  </template>
</info-box>

<!-- Menampilkan props -->
---
author:
  name: Benjamin agung hidayat
  bio: All about Benjamin

---
penulis:
  name: contoh nama penulis
  bio: Penulis buku terkenal

---
text: coba dulu

<author-info :author="{name: 'name', bio:'bio'}" :text="'text'" />

## This is a heading

This is some more info

### This is a sub heading

This is some more info

### This is another sub heading

This is some more info

## This is another heading

This is some more info
