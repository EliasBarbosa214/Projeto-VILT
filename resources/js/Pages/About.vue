<template>
    <Head>
        <title>Sobre</title>
        <meta name="Página Home" content="Página Home" />
    </Head>
    <div>
        <div class="px-4 sm:px-6 lg:px- mb-6">
            <div class="sm:flex sm:items-center">
                <div class="sm:flex-auto mt-6">
                    <h1 class="text-xl font-semibold text-gray-900 uppercase">
                        Página About
                    </h1>
                </div>
                <hr />

                <layout-menu />
            </div>
        </div>

        <div class="text-center py-3">
            <p>{{ name }} está fazendo o curso de {{ curso }}!</p>
        </div>
    </div>
</template>

<script>
import LayoutMenu from "../Layouts/LayoutMenu.vue";
import { Head } from "@inertiajs/inertia-vue3";
export default {
    name: "pageAbout",
    props: {
        name: String,
        curso: String,
    },
    components: {
        LayoutMenu,
        Head,
    },
};
</script>

<style scoped></style>
