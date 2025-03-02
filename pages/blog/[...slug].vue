<template>
    <article class="prose dark:prose-invert">
        <ContentDoc v-if="route.params.slug" />
    </article>
</template>

<script setup>

const route = useRoute()
console.log(route.params.slug);
function toggleLayout() {
    setPageLayout('another')
}
</script>