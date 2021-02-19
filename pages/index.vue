<template>
    <div>
        <link rel="preconnect" href="https://fonts.gstatic.com">
        <link href="https://fonts.googleapis.com/css?family=Cabin|Roboto:400,700|Roboto+Condensed:400,700" rel="stylesheet">
        <header class="fixed z-10">
            <nav class="nav fixed w-full flex text-2xl bg-blur">
                <a class="active block py-4 px-8 hover:text-black text-black" href="#">Home</a>
                <a class="block text-white py-4 px-8 hover:bg-black hover:text-black" href="#">Home</a>
                <a class="block text-white py-4 px-8 hover:bg-black hover:text-black" href="#">MX Maps</a>
                <a class="block text-white py-4 px-8 hover:bg-black hover:text-black" href="#">Members</a>
            </nav>
        </header>
        <article class="flex flex-col items-center justify-center px-8 a-1 bg-cover bg-center w-full py-32">
            <div class="p-8 w-full md:w-2/3 lg:w-3/5 xl:1/2">
                <h2 class="mb-4 capped-top-left bg-blur inline-block text-5xl px-8 py-4 pr-8">
                    {{ page.title }}
                </h2>
                <div class="capped-top-left bg-blur px-8 py-4">
                    <nuxt-content :document="page" />
                </div>
            </div>
        </article>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
    async asyncData ({ $content }) {
        const page = await $content('hello').fetch()
        return {
            page
        }
    },
    data: () => ({
        page: null
    }),
})
</script>

<style>
.a-1 {
    background-image: url(https://i.imgur.com/hksOZUJ.png);
}

.bg-blur {
    backdrop-filter: blur(5px);
}

.nav {
    background-image: linear-gradient(10deg, #000000BB, #00000099, #00000033);
}
.nav a.active, a:hover {
    background-image: linear-gradient(135deg, transparent 1rem, white 1rem, white)
}

.capped-top-left {
    background-image: linear-gradient(135deg, transparent 1rem, #FFFFFF99 1rem, #FFFFFFEE, #FFFFFF33);
}
</style>
