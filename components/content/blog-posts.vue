<template>
    <section class="not-prose">
        <h1>Blog Page</h1>
        <ul>
            <li v-for="item in result" :key="item._path">
                <NuxtLink :to="item._path">{{ item.title }}</NuxtLink>
            </li>
        </ul>
    </section>
</template>

<script setup>
// Remove definePageMeta - it's for pages only, not components

// Use a single useAsyncData call
const { data: result } = await useAsyncData('blog-list',
    () => queryContent('/blog')
        .where({ _path: { $ne: '/blog' } })
        .only(['_path', 'title'])
        .find()
);
</script>