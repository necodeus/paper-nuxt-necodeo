<template>
    <ul class="font-jost inline-flex flex-col gap-[30px] p-[30px] component-border-bottom w-full">
        <li v-for="post in posts" v-bind:key="post.id">
            <div class="flex items-center">
                <a :href="post.author_path || '#'" class="flex items-center">
                    <picture>
                        <img :src="post.author_picture?.['25x25']" alt="" loading="lazy"
                            class="min-w-[25px] max-w-[25px] min-h-[25px] max-h-[25px] bg-cover bg-center !rounded-[50%] bg-[#eee] object-cover" />
                    </picture>
                    <span class="ml-[10px] text-[16px]">
                        <b class="font-medium">{{ post.author_name }}</b>
                    </span>
                </a>
                <div v-if="post.created_at" class="divSeparator"></div>
                <span v-if="post.created_at" class="text-[16px]">{{ moment(post.created_at).fromNow() }}</span>
            </div>
            <h1 class="flex mt-[10px]">
                <NuxtLink :to="post.path || ''" class="text-[38px]"> {{ post.title }}</NuxtLink>
            </h1>
        </li>
    </ul>
</template>

<script setup>
import moment from "moment/min/moment-with-locales"
moment.locale("pl")

defineProps({
    posts: {
        type: Array,
        required: true,
        default: () => [],
    },
})
</script>

<style styled>
.list:not(:last-child) {
    margin-bottom: 30px;
}

.div-separator {
    background-color: black;
    border-radius: 999px;
    width: 3px;
    height: 3px;
    min-width: 3px;
    min-height: 3px;
    max-width: 3px;
    max-height: 3px;
    margin: 0 10px;
    display: flex;
    opacity: 0.5;
}
</style>
