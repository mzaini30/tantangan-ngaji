# Template Vue

## Menggunakan Vue Editor

Tambahkan di `~/.bashrc`:

```bash
export VUE_EDITOR=subl
```

## Meletakkan File-File Vue dan Markdown

Di folder `src/pages/`.

## Meletakkan File-File Static

Di folder `public/`.

## Mengubah Base URL (untuk keperluan sitemap)

Pada file `vite.config.js`, pada bagian:

```javascript
const hostname = 'http://localhost:3000/'
```

## Contoh File Markdown dengan Head

```markdown
---
title: About
---

# Ini adalah Halaman About

Lumayan
```

## Ngelink ke Halaman Lain

```html
<router-link to="/about">Halaman About</router-link>
```

## Contoh Menggunakan Head pada Halaman Vue

```html
<script setup="">
	import {Head} from '@vueuse/head'
</script>

<template>
	<Head>
		<title>Hai...</title>
	</Head>

	<p>Ini adalah bagian beranda</p>
</template>
```