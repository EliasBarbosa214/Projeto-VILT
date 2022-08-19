<script setup>
import { Head, Link } from "@inertiajs/inertia-vue3";
import JetApplicationMark from "@/Components/ApplicationMark.vue";

defineProps({
    canLogin: Boolean,
    canRegister: Boolean,
    laravelVersion: String,
    phpVersion: String,
});
</script>

<template>
    <Head title="Bem Vindo" />

    <div
        class="relative flex items-top justify-center min-h-screen bg-gray-100 dark:bg-gray-900 sm:items-center sm:pt-0"
    >
        <div
            v-if="canLogin"
            class="hidden fixed top-0 right-0 px-6 py-4 sm:block"
        >
            <Link
                v-if="$page.props.user"
                :href="route('dashboard')"
                class="text-sm text-gray-700 dark:text-gray-500 underline"
                >Dashboard</Link
            >

            <template v-else>
                <Link
                    :href="route('login')"
                    class="text-sm text-gray-700 dark:text-gray-500 underline"
                    >Log in</Link
                >

                <Link
                    v-if="canRegister"
                    :href="route('register')"
                    class="ml-4 text-sm text-gray-700 dark:text-gray-500 underline"
                    >Register</Link
                >
            </template>
        </div>

        <div class="max-w-6xl mx-auto mt-6 sm:px-6 lg:px-8">
            <div>
                <div class="flex justify-center pt-8 sm:pt-0">
                    <div class="shrink-0 flex items-center">
                        <Link :href="route('dashboard')">
                            <JetApplicationMark class="block h-20 w-auto" />
                        </Link>
                    </div>
                </div>

                <div class="text-center mt-4 uppercase">
                    <h1 class="text-lg">
                        Bem Vindo(a) ao Projeto de VILT <br />
                        <span class="font-bold text-2xl">
                            (<span class="text-green-500"
                                ><span class="text-4xl">V</span>ue</span
                            >,
                            <span class="text-indigo-500"
                                ><span class="text-4xl">I</span>nertia</span
                            >,
                            <span class="text-red-500"
                                ><span class="text-4xl">L</span>aravel</span
                            >
                            e
                            <span class="text-sky-400"
                                ><span class="text-4xl">T</span>ailwind</span
                            >
                            )</span
                        >
                    </h1>
                </div>
            </div>

            <br />

            <div
                class="relative max-w-md mx-auto md:max-w-2xl min-w-0 break-words bg-white w-full mb-16 shadow-lg rounded-xl mt-20"
            >
                <div class="px-6">
                    <div class="flex flex-wrap justify-center">
                        <div class="w-full flex justify-center">
                            <div class="relative">
                                <img
                                    src="../Images/foto-perfil.jpg"
                                    class="shadow-xl rounded-full align-middle border-none absolute -m-16 -ml-20 lg:-ml-16 max-w-[150px]"
                                />
                            </div>
                        </div>
                        <div class="w-full text-center mt-20">
                            <div class="flex justify-center lg:pt-4 pt-8 pb-0">
                                <div class="p-3 text-center">
                                    <a
                                        href="https://www.linkedin.com/in/elias-barbosa-oficial/"
                                        target="_blank"
                                        ><span
                                            class="text-xl font-bold block uppercase tracking-wide text-slate-700 hover:text-blue-600 hover:text-2xl"
                                            style="transition: all 0.3s"
                                            >LinkedIn</span
                                        >
                                    </a>
                                </div>
                                <div class="p-3 text-center">
                                    <a
                                        href="mailto:eliasbarbosasousa214@gmail.com"
                                        ><span
                                            class="text-xl font-bold block uppercase tracking-wide text-slate-700 hover:text-red-600 hover:text-2xl"
                                            style="transition: all 0.3s"
                                            >E-mail</span
                                        ></a
                                    >
                                </div>

                                <div class="p-3 text-center">
                                    <a
                                        href="https://github.com/EliasBarbosa214"
                                        target="_blank"
                                    >
                                        <span
                                            class="text-xl font-bold block uppercase tracking-wide text-slate-700 hover:text-green-600 hover:text-2xl"
                                            style="transition: all 0.3s"
                                            >GitHub</span
                                        >
                                    </a>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="text-center mt-2">
                        <h3
                            class="text-2xl text-slate-700 font-bold leading-normal mb-1"
                        >
                            Elias Barbosa de Sousa
                        </h3>
                        <div
                            class="text-xs mt-0 mb-2 text-slate-400 font-bold uppercase"
                        >
                            <i
                                class="fas fa-map-marker-alt mr-2 text-slate-400 opacity-75"
                            ></i
                            >Brasil, Rio de Janeiro
                        </div>
                    </div>
                    <div
                        class="mt-6 py-6 border-t border-slate-200 text-center"
                    >
                        <div class="flex flex-wrap justify-center">
                            <div class="w-full px-4">
                                <p
                                    class="font-light leading-relaxed text-slate-600 mb-4"
                                >
                                    Sou um Desenvolvedor Front-End e estudo
                                    Sistemas de Informações na Unigranrio. Sou
                                    especializado em Vue.js 3 com Tailwind, em
                                    aprendizado PHP, Laravel e agora Inertia.

                                    <br /><br />

                                    Minhas habilidades são: HTML, CSS,
                                    JavaScript, Vue.js 2 e 3, TailwindCSS, PHP,
                                    Laravel 9 e Inertia.js
                                </p>
                                <a
                                    href="https://github.com/EliasBarbosa214/Projeto-VILT"
                                    target="_blank"
                                    class="font-normal text-slate-700 hover:text-slate-400"
                                    >GITHUB: PROJETO VILT</a
                                >
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <footer class="bg-gray-200 shadow-xl text-center lg:text-left font-bold">
        <div class="text-indigo-500 text-center p-4">
            2022 © Copyright:
            <a
                class="hover:text-indigo-800 transition duration-300"
                href="https://www.linkedin.com/in/elias-barbosa-oficial/"
                >Elias Barbosa de Sousa</a
            >
        </div>
    </footer>
</template>
