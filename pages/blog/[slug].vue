<template>
    <div>
        <h1>Inside Blog Post</h1>
    </div>
    <div>
        <h2>Post id is{{ route.params.slug }}</h2>
    </div>
    <button @click="toggleLayout">Back</button>
</template>

<script setup>
const route = useRoute()
console.log(route);
function toggleLayout() {
    setPageLayout('another')
}
</script>