<template>
    <p class="mb-10">Take a lok at my GitHub projects!</p>
    <section v-if="pending">Loding...</section>
    <section v-else-if="error">Something went wrong... Tr again!</section>

    <section v-else>
        <ul class="grid grid-cols-1 gap-4">
            <li v-for="repository in repos" :key="repository.id" class="border border-gray-200 rounded-sm p-4 hover:bg-gray-100">
                <a :href="repository.html_url" target="_blank"> // trget blank is used to open the link in new tab
                    <div class="flex items-center justify-between">
                        <div class="font-semibold">
                            {{ repository.name }}
                        </div>
                        <div>{{ repository.stargazers_count }}★ </div>
                    </div>
                    <p class="text-sm">{{ repository.description }}</p>
                </a>
            </li>
        </ul>
    </section>

</template>

<script setup>
console.log()
const { error, pending, data } = await useFetch('https://api.github.com/users/piotr-jura-udemy/repos');

const repos = computed(() => {
    return data.value.filter((repo) => repo.description).sort((a, b) => b.stargazers_count - a.stargazers_count);
})
</script>
