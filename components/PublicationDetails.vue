<script setup>
import moment from 'moment/min/moment-with-locales'
moment.locale('pl')

const { publisher, createdAt } = defineProps({
    publisher: {
        type: Object,
        required: false,
        default: () => null,
    },
    createdAt: {
        type: String,
        required: true,
    },
});
</script>

<template>
    <div class="relative !py-0 flex items-center mb-[10px]">
        <NuxtLink v-if="publisher" :to="publisher.path || ''" class="flex items-center">
            <img :src="publisher.picture?.['25x25']" alt="" loading="lazy"
                class="min-w-[25px] max-w-[25px] min-h-[25px] max-h-[25px] bg-cover bg-center !rounded-[50%] bg-[#eee] object-cover" />
            <div class="ml-[10px] font-medium">
                {{ publisher.name }}
            </div>
        </NuxtLink>
        <div class="divSeparator"></div>
        <div>
            {{ moment(createdAt).fromNow() }}
        </div>
    </div>
</template>

<style>
.divSeparator {
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