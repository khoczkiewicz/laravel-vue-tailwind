# Introduction

This is an example of Laravel 11 + Vue 3.5 + Tailwind 4.0 project with installation and configuration steps.

# Installation

## Laravel

At the beginning create a Laravel project and provide Vue framework:

```sh
composer create-project laravel/laravel laravel-vue-tailwind
yarn add vue

```

## Vite

Now add Vite in order to:
- speed up development with HMR
- optimize production builds
- work out of the box with Vue & Tailwind
- have native Laravel support

```sh
yarn add @vitejs/plugin-vue
```

## Tailwind

Finally add Tailwind:

```sh
yarn add --dev tailwindcss
```

And additions to transform styles with JS plugins:

```sh
yarn add --dev @tailwindcss/postcss postcss autoprefixer
```

# Configuration

## Vite

In `vite.config.js` import `vue` from `@vitejs/plugin-vue` and add `vue()` to plugins.

## Vue component

Then create entry point for Vue replacing content of `resources/js/app.js` with:

```js
import { createApp } from 'vue';
import App from './components/App.vue';

createApp(App).mount('#app');
```

`bootstrap.js` can be removed if created.

Afterall add component `App.vue` in `resource/js/components` with some template like:

```html
<template>
    <div class="p-6 bg-gray-200 text-center text-xl font-bold">
        Welcome to Laravel 11 + Vue 3.5 + Tailwind 4.0!
    </div>
</template>

<script>
export default {
    name: "App",
};
</script>

<style scoped></style>
```

## Blade view

Afterall you can replace your `welcome.blade.php` view with:

```php
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laravel Vue App</title>
    @vite(['resources/css/app.css', 'resources/js/app.js'])
</head>

<body class="bg-gray-100">
    <div id="app"></div>
</body>

</html>
```

## Tailwind

In the end make sure that in `postcss.config.js` you have `@tailwindcss/postcss` instead of `tailwindcss` plugin.

And let's import Tailwind in `app.css` with:

```css
@import "tailwindcss";
```

# Run

```sh
composer install
yarn
yarn build
php artisan serve
```