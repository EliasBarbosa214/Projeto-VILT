<script>
import AppLayout from "@/Layouts/AppLayout.vue";
import { Link, Head, useForm } from "@inertiajs/inertia-vue3";

export default {
    components: {
        AppLayout,
        Link,
        Head,
        useForm,
    },
    props: {
        errors: Object,
        post: Object,
    },
    data(props) {
        const form = useForm(props.post);

        return {
            form,
        };
    },
};
</script>

<template>
    <Head>
        <title>Editando Postagem</title>
        <meta name="Página Edit Post" content="Página Edit Post" />
    </Head>

    <AppLayout title="Editando Postagem">
        <template #header>
            <h2
                class="font-semibold text-xl text-gray-800 leading-tight uppercase"
            >
                Editando Postagem
            </h2>
        </template>

        <div class="py-6">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div
                    class="bg-white p-8 overflow-hidden shadow-lg sm:rounded-lg"
                >
                    <!-- FORM -->
                    <form
                        @submit.prevent="
                            form.put(route('dashboard.update', form.id))
                        "
                    >
                        <div class="mb-6">
                            <label
                                for="titleId"
                                class="text-sm font-medium text-gray-900 block mb-2"
                                >Título</label
                            >
                            <input
                                v-model="form.title"
                                type="text"
                                id="titleId"
                                class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
                                placeholder="Exemplo: Discussão sobre..."
                            />
                            <div v-if="errors.title" class="text-red-600">
                                {{ errors.title }}
                            </div>
                        </div>
                        <div class="mb-6">
                            <label
                                for="descId"
                                class="text-sm font-medium text-gray-900 block mb-2"
                                >Descrição</label
                            >

                            <textarea
                                v-model="form.content"
                                name=""
                                id="descId"
                                cols="30"
                                rows="10"
                                class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
                                placeholder="Exemplo: Gostaria de conversar sobre..."
                            ></textarea>
                            <div v-if="errors.content" class="text-red-600">
                                {{ errors.content }}
                            </div>
                        </div>

                        <div class="flex-shrink-0 p-4 pl-0">
                            <button
                                type="submit"
                                class="inline-flex items-center p-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm bg-indigo-500 hover:bg-blue-800 transition duration-150 text-white"
                            >
                                Editar Post
                            </button>

                            <Link :href="route('dashboard')">
                                <button
                                    type="submit"
                                    class="inline-flex ml-2 items-center p-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm bg-red-500 hover:bg-red-800 transition duration-150 text-white"
                                >
                                    Cancelar
                                </button>
                            </Link>
                        </div>
                    </form>
                    <!-- FIM FORM -->
                </div>
            </div>
        </div>
    </AppLayout>
</template>

<style>
@media (min-width: 640px) {
    table {
        display: inline-table !important;
    }

    thead tr:not(:first-child) {
        display: none;
    }
}

td:not(:last-child) {
    border-bottom: 0;
}

th:not(:last-child) {
    border-bottom: 2px solid rgba(0, 0, 0, 0.1);
}
</style>
