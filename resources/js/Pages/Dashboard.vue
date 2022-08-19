<script setup>
import AppLayout from "@/Layouts/AppLayout.vue";
import Welcome from "@/Components/Welcome.vue";
</script>

<script>
import { Link } from "@inertiajs/inertia-vue3";
import { Inertia } from "@inertiajs/inertia";
export default {
    name: "pageDashboard",
    props: {
        posts: Object,
    },
    components: {
        Link,
    },
    data() {
        const destroy = (id) => {
            if (confirm("Tem certeza que deseja excluir?")) {
                Inertia.delete(route("dashboard.destroy", id));
            }
        };

        return {
            destroy,
        };
    },
};
</script>

<template>
    <AppLayout title="Dashboard">
        <template #header>
            <h2
                class="font-semibold text-xl text-gray-800 leading-tight uppercase"
            >
                Listagem de Postagens - Bem Vindo(a) {{ $page.props.user.name }}
            </h2>

            <h3
                class="font-semibold text-xs mt-2 text-gray-600 leading-tight uppercase"
            >
                {{ $page.props.user.email }}
            </h3>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto">
                <div
                    class="bg-white overflow-hidden shadow-xl sm:rounded-lg mb-6 py-3 px-4"
                >
                    <div class="">
                        <!-- Outline -->
                        <Link :href="route('dashboard.create')">
                            <button
                                class="px-4 py-2 bg-transparent outline-none border-2 border-indigo-400 rounded text-indigo-500 font-medium active:scale-95 hover:bg-indigo-600 hover:text-white hover:border-transparent focus:bg-indigo-600 focus:text-white focus:border-transparent focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2 disabled:bg-gray-400/80 disabled:shadow-none disabled:cursor-not-allowed transition-colors duration-200"
                            >
                                Criar Post
                            </button>
                        </Link>

                        <div
                            v-if="$page.props.flash.messageCreate"
                            class="flex bg-green-100 rounded-lg p-4 mb-4 mt-4 text-sm text-green-500"
                            role="alert"
                        >
                            <svg
                                class="w-5 h-5 inline mr-3"
                                fill="currentColor"
                                viewBox="0 0 20 20"
                                xmlns="http://www.w3.org/2000/svg"
                            >
                                <path
                                    fill-rule="evenodd"
                                    d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 11-2 0 1 1 0 012 0zM9 9a1 1 0 000 2v3a1 1 0 001 1h1a1 1 0 100-2v-3a1 1 0 00-1-1H9z"
                                    clip-rule="evenodd"
                                ></path>
                            </svg>
                            <div>
                                {{ $page.props.flash.messageCreate }}
                            </div>
                        </div>

                        <div
                            v-if="$page.props.flash.messageDelete"
                            class="flex bg-red-100 rounded-lg p-4 mb-4 mt-4 text-sm text-red-600"
                            role="alert"
                        >
                            <svg
                                class="w-5 h-5 inline mr-3"
                                fill="currentColor"
                                viewBox="0 0 20 20"
                                xmlns="http://www.w3.org/2000/svg"
                            >
                                <path
                                    fill-rule="evenodd"
                                    d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 11-2 0 1 1 0 012 0zM9 9a1 1 0 000 2v3a1 1 0 001 1h1a1 1 0 100-2v-3a1 1 0 00-1-1H9z"
                                    clip-rule="evenodd"
                                ></path>
                            </svg>
                            <div>
                                {{ $page.props.flash.messageDelete }}
                            </div>
                        </div>

                        <div
                            v-if="$page.props.flash.messageUpdate"
                            class="flex bg-blue-100 rounded-lg p-4 mb-4 mt-4 text-sm text-blue-600"
                            role="alert"
                        >
                            <svg
                                class="w-5 h-5 inline mr-3"
                                fill="currentColor"
                                viewBox="0 0 20 20"
                                xmlns="http://www.w3.org/2000/svg"
                            >
                                <path
                                    fill-rule="evenodd"
                                    d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 11-2 0 1 1 0 012 0zM9 9a1 1 0 000 2v3a1 1 0 001 1h1a1 1 0 100-2v-3a1 1 0 00-1-1H9z"
                                    clip-rule="evenodd"
                                ></path>
                            </svg>
                            <div>
                                {{ $page.props.flash.messageUpdate }}
                            </div>
                        </div>
                    </div>
                </div>

                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    <section class="relative py-3 max-h-96 overflow-auto">
                        <div class="w-full px-4">
                            <div
                                class="relative flex flex-col min-w-0 break-words w-full shadow-lg rounded bg-indigo-900 text-white"
                            >
                                <div class="block w-full overflow-x-auto">
                                    <table
                                        class="items-center w-full bg-transparent border-collapse"
                                    >
                                        <thead>
                                            <tr>
                                                <th
                                                    class="px-6 align-middle border border-solid py-3 text-xs uppercase border-l-0 border-r-0 border-t-0 whitespace-nowrap font-semibold text-left bg-indigo-700 text-blue-100 border-indigo-600 rounded-tl"
                                                >
                                                    ID
                                                </th>
                                                <th
                                                    class="px-6 align-middle border border-solid py-3 text-xs uppercase border-l-0 border-r-0 whitespace-nowrap font-semibold text-left bg-indigo-700 text-blue-100 border-indigo-500"
                                                >
                                                    TITLE
                                                </th>
                                                <th
                                                    class="px-6 align-middle border border-solid py-3 text-xs uppercase border-l-0 border-r-0 whitespace-nowrap font-semibold text-left bg-indigo-700 text-blue-100 border-indigo-600"
                                                >
                                                    CONTENT
                                                </th>

                                                <th
                                                    class="px-6 align-middle border border-solid py-3 text-xs uppercase border-l-0 border-r-0 whitespace-nowrap font-semibold text-left bg-indigo-700 text-blue-100 border-indigo-600"
                                                >
                                                    CREATED_AT / UPDATE_AT
                                                </th>
                                                <th
                                                    class="px-6 align-middle border border-solid py-3 text-xs uppercase border-l-0 border-r-0 border-t-0 whitespace-nowrap font-semibold text-left bg-indigo-700 text-blue-100 border-indigo-600 rounded-tr"
                                                >
                                                    ACTIONS
                                                </th>
                                            </tr>
                                        </thead>

                                        <tbody>
                                            <tr
                                                v-for="post in posts"
                                                :key="post.id"
                                            >
                                                <th
                                                    class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-nowrap p-4 text-left"
                                                >
                                                    <div
                                                        class="bg-indigo-500 w-10 h-10 rounded-full items-center text-center"
                                                        style="
                                                            justify-content: center;
                                                            display: -webkit-flex;
                                                            display: -ms-flexbox;
                                                            display: flex;

                                                            -webkit-align-items: center;
                                                            -webkit-box-align: center;
                                                            -ms-flex-align: center;
                                                            align-items: center;
                                                        "
                                                    >
                                                        <span
                                                            class="font-bold text-white items-center"
                                                        >
                                                            {{ post.id }}
                                                        </span>
                                                    </div>
                                                </th>
                                                <td
                                                    class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-nowrap p-4"
                                                >
                                                    {{ post.title }}
                                                </td>
                                                <td
                                                    class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-nowrap p-4"
                                                >
                                                    <div
                                                        class="w-96 overflow-auto"
                                                    >
                                                        {{ post.content }}
                                                    </div>
                                                </td>

                                                <td
                                                    class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-nowrap p-4"
                                                >
                                                    <div
                                                        class="w-64 overflow-auto"
                                                    >
                                                        <span class="font-bold"
                                                            >CREATED:</span
                                                        >
                                                        {{ post.created_at }}
                                                        <br />
                                                        <span class="font-bold"
                                                            >UPDATED:</span
                                                        >
                                                        {{ post.updated_at }}
                                                    </div>
                                                </td>

                                                <td
                                                    class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-nowrap p-4"
                                                >
                                                    <button
                                                        @click="
                                                            destroy(post.id)
                                                        "
                                                        type="submit"
                                                        class="py-2 px-6 bg-red-700 hover:bg-red-600 rounded hover:shadow-lg font-semibold"
                                                        style="
                                                            transition: 0.3s all;
                                                        "
                                                    >
                                                        DELETE
                                                    </button>

                                                    <Link
                                                        :href="
                                                            route(
                                                                'dashboard.edit',
                                                                post.id
                                                            )
                                                        "
                                                    >
                                                        <button
                                                            class="py-2 px-6 ml-2 bg-blue-700 hover:bg-blue-600 rounded hover:shadow-lg font-semibold"
                                                            style="
                                                                transition: 0.3s
                                                                    all;
                                                            "
                                                        >
                                                            EDIT
                                                        </button>
                                                    </Link>
                                                </td>
                                            </tr>
                                        </tbody>
                                    </table>
                                </div>
                            </div>
                        </div>
                    </section>
                </div>
            </div>
        </div>
    </AppLayout>
</template>

<style scoped>
tr:nth-child(odd) {
    background: rgba(0, 0, 0, 0.2);
}

tr:nth-child(even) {
    background: rgba(0, 0, 0, 0.1);
}

tr:nth-child(odd):hover {
    background: rgba(0, 0, 0, 0.4);
}

tr:nth-child(even):hover {
    background: rgba(0, 0, 0, 0.4);
}
</style>
