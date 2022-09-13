<script setup>
    import BreezeAuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
    import { Head } from "@inertiajs/inertia-vue3";
    import BreezeButton from "@/Components/PrimaryButton.vue";
    import { Link } from "@inertiajs/inertia-vue3";
    import { useForm } from "@inertiajs/inertia-vue3";

    const props = defineProps({
        book: {
            type: Object,
            default: () => ({}),
        },
    });

    const form = useForm({
        id: props.book.id,
        title: props.book.title,
        autor: props.book.autor,
        review: props.book.review,
    });


    const submit = () => {
        form.put(route("books.update", props.book.id));
    };
    </script>

    <template>
        <Head title="Book Edit" />

        <BreezeAuthenticatedLayout>
            <template #header>
                <h2 class="text-xl font-semibold leading-tight text-gray-800">
                    Book Edit
                </h2>
            </template>

            <div class="py-12">
                <div class="mx-auto max-w-7xl sm:px-6 lg:px-8">
                    <div class="overflow-hidden bg-white shadow-sm sm:rounded-lg">
                        <div class="p-6 bg-white border-b border-gray-200">
                            <form @submit.prevent="submit">
                                <div class="mb-6">
                                    <label
                                        for="Title"
                                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                                        >Title</label
                                    >
                                    <input
                                        type="text"
                                        v-model="form.title"
                                        name="title"
                                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
                                        placeholder=""
                                    />
                                    <div
                                        v-if="form.errors.title"
                                        class="text-sm text-red-600"
                                    >
                                        {{ form.errors.title }}
                                    </div>
                                </div>
                                <div class="mb-6">
                                    <label
                                        for="Autor"
                                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                                        >Autor</label
                                    >
                                    <input
                                        type="text"
                                        v-model="form.autor"
                                        name="autor"
                                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
                                        placeholder=""
                                    />
                                    <div
                                        v-if="form.errors.autor"
                                        class="text-sm text-red-600"
                                    >
                                        {{ form.errors.autor }}
                                    </div>
                                </div>
                                <div class="mb-6">
                                    <label
                                        for="review"
                                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                                        >Review</label
                                    >
                                    <textarea
                                        type="text"
                                        v-model="form.review"
                                        name="review"
                                        id=""
                                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
                                    ></textarea>

                                    <div
                                        v-if="form.errors.review"
                                        class="text-sm text-red-600"
                                    >
                                        {{ form.errors.review }}
                                    </div>
                                </div>
                                <button
                                    type="submit"
                                    class="text-white bg-blue-700  focus:outline-none  font-medium rounded-lg text-sm px-5 py-2.5 "
                                    :disabled="form.processing"
                                    :class="{ 'opacity-25': form.processing }"
                                >
                                    Submit
                                </button>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </BreezeAuthenticatedLayout>
    </template>
