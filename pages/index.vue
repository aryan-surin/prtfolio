<template>
  <div>
    <h1>Home Page</h1>
  </div>
</template>

<script setup>
useSeoMeta({
  title: 'Main Page',
  description: 'This is the main page of the website',
  ogTitle: 'Main Page',
  ogDescription: 'This is the main page of the website',
  ogImage: '[og:image]',
  ogUrl: '[og:url]',
  twitterTitle: '[twitter:title]',
  twitterDescription: '[twitter:description]',
  twitterImage: '[twitter:image]',
  twitterCard: 'summary'
})

useHead({
  htmlAttrs: {
    lang: 'en'
  },
  link: [
    {
      rel: 'icon',
      type: 'image/png',
      href: '/favicon.png'
    }
  ]
})
</script>