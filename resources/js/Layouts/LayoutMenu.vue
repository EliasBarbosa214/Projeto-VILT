<template>
    <nav>
        <div class="mt-4">
            <Link
                :href="route('home')"
                :class="{ 'font-bold': $page.url === '/home' }"
                >Post</Link
            >
            -
            <Link
                :href="route('about')"
                :class="{ 'font-bold': $page.url === '/about' }"
                >Sobre</Link
            >
        </div>
    </nav>
</template>

<script>
import { Link } from "@inertiajs/inertia-vue3";

export default {
    name: "layoutMenu",
    components: {
        Link,
    },
};
</script>

<style></style>
