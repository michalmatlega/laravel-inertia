<template>
    <Link href="/">Main Page</Link>
    <Link href="/hello">Show Page</Link>
    <Link href="/listing">Listings</Link>
    <Link href="/listing/create">Create</Link>
    <div v-if="flashSuccess" class="success">
        {{ flashSuccess }}
    </div>
    <div>The page with time {{ timer }}</div>
    <slot>Default</slot>
</template>

<script setup>
import {Link, usePage} from '@inertiajs/vue3';
import {ref, computed} from "vue";

const page = usePage();
const timer = ref(0);
setInterval(() => {
    timer.value += 1;
}, 1000);

const flashSuccess = computed(() => {
    console.log(page.props);
    return page.props.flash.success;
});
</script>

<style scoped>
    .success {
        background-color: green;
    }
</style>
