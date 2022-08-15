<template >
    <app-layout>
            <h1 class="text-center text-2xl font-bold leading-7 text-gray-500 sm:text-3xl sm:truncate py-4 ">Usuarios</h1>

            <div class="py-12">
                <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                    <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                        <inertia-link
                            :href="route('users.create')"
                            class="flex-shrink-0 bg-gray-600 hover:bg-gray-500 cursor-pointer text-white text-base font-semibold py-2 px-4 rounded-lg shadow-md m-4"
                            type="button" >
                            Crear Usuario
                        </inertia-link>

                        <table class="rounded-t-lg mt-5 min-w-full mx-auto bg-gray-800 text-gray-100">
                            <thead>
                                <tr>
                                    <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-100 uppercase tracking-wider">Nombre</th>
                                    <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-100 uppercase tracking-wider">Username</th>
                                    <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-100 uppercase tracking-wider">Email</th>
                                    </tr>
                            </thead>
                            <tbody class="bg-gray-700 border-b border-gray-600 text-gray-200 ">
                                <tr v-for="user in users" :key="user.id"
                                >

                                    <td class="px-6 py-4 whitespace-nowrap"><div class="text-sm">{{ user.name }}</div></td>
                                    <td class="px-6 py-4 whitespace-nowrap"><div class="text-sm">{{ user.username }}</div></td>
                                    <td class="px-6 py-4 whitespace-nowrap"><div class="text-sm">{{ user.email }}</div></td>

                                    <td class="flex m-2 gap-4">
                                        <inertia-link
                                            :href="route('users.edit', user.id)"
                                            class="flex-shrink-0 bg-purple-600 text-white text-base font-semibold py-2 px-4 rounded-lg shadow-md hover:bg-purple-700 focus:outline-none cursor-pointer"
                                            >
                                            Editar
                                        </inertia-link>
                                        <inertia-link
                                            method="delete"
                                            :href="route('users.destroy', user.id)"
                                            class="flex-shrink-0 bg-red-600 text-white text-base font-semibold py-2 px-4 rounded-lg shadow-md hover:bg-red-700 focus:outline-none cursor-pointer"
                                            >
                                            Eliminar
                                        </inertia-link>
                                    </td>
                                </tr>

                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
    </app-layout>
</template>
    
<script>
import AppLayout from "@/Layouts/AppLayout.vue";
export default {
    props:{
        users: Array
    },
    components:{
        AppLayout
    }
}
</script>