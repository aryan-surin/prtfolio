<template>
    <section class="not-prose font-mono">
        <div class="column text-gray-400 text-sm">
            <div>date</div>
            <div>title</div>
        </div>
        <ul>
            <li v-for="item in result" :key="item._path">
                <NuxtLink :to="item._path" class="column hover:text-blue-500 dark:hover:text-blue-400">
                    <div class="text-gray-500">2023</div>
                    <div>{{ item.title }}</div>
                </NuxtLink>
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

<style scoped>
.column {
    @apply flex items-center space-x-8 py-2 border-b border-gray-200 dark:border-gray-700;
}
</style>