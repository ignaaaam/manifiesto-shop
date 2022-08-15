<template >
    <app-layout>
            <h1 class="text-center text-2xl font-bold leading-7 text-gray-500 sm:text-3xl sm:truncate py-4 ">Mostrar todos los productos</h1>

            <div class="py-12">
                <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                    <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                        <inertia-link
                            :href="route('products.create')"
                            class="flex-shrink-0 bg-gray-600 hover:bg-gray-500 cursor-pointer text-white text-base font-semibold py-2 px-4 rounded-lg shadow-md m-4"
                            type="button" >
                            Crear Producto
                        </inertia-link>

                        <table class="rounded-t-lg mt-5 min-w-full mx-auto bg-gray-800 text-gray-100">
                            <thead>
                                <tr>
                                    <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-100 uppercase tracking-wider"></th>
                                    <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-100 uppercase tracking-wider">Nombre</th>
                                    <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-100 uppercase tracking-wider">Descripción</th>
                                    <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-100 uppercase tracking-wider">Precio</th>
                                    <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-100 uppercase tracking-wider">Stock</th>
                                    <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-100 uppercase tracking-wider">Estado</th>
                                    </tr>
                            </thead>
                            <tbody class="bg-gray-700 border-b border-gray-600 text-gray-200 ">
                                <tr v-for="product in products" :key="product.id" :disabled="product.stock <= 0 || product.state == 0"
                                >

                                    <td class="px-6 py-4 whitespace-nowrap"><div class="text-sm">{{ product.thumbnail }}</div></td>
                                    <td class="px-6 py-4 whitespace-nowrap"><div class="text-sm">{{ product.name }}</div></td>
                                    <td class="px-6 py-4 whitespace-nowrap"><div class="text-sm">{{ product.description }}</div></td>
                                    <td class="px-6 py-4 whitespace-nowrap"><div class="text-sm">{{ product.price }} <span>€</span></div> </td>
                                    <td class="px-6 py-4 whitespace-nowrap"><div class="text-sm">{{ product.stock }}</div></td>
                                    <td class="px-6 py-4 whitespace-nowrap"><div class="text-sm">{{ product.state }}</div></td>

                                    <td class="flex m-2 gap-4">
                                        <inertia-link
                                            :href="route('products.edit', product.id)"
                                            class="flex-shrink-0 bg-purple-600 text-white text-base font-semibold py-2 px-4 rounded-lg shadow-md hover:bg-purple-700 focus:outline-none cursor-pointer"
                                            >
                                            Editar
                                        </inertia-link>
                                        <inertia-link
                                            method="delete"
                                            :href="route('products.destroy', product.id)"
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
        products: Array
    },
    components:{
        AppLayout
    }
}
</script>