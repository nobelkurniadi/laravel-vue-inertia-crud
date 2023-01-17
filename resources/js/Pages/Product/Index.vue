<template>
    <div v-if="$page.props.flash.message" class="alert alert-success alert-dismissible fade show" role="alert">
        <strong>{{ $page.props.flash.message }}</strong>
        <button type="button" class="btn-close" data-bs-dismiss="alert" aria-label="Close"></button>
    </div>
    <div class="card">

        <div class="card-header">
            <inertia-link href="/product/create" class="btn btn-primary">Add Product</inertia-link>
        </div>
        <div class="card-body">
            <table class="table table-hover">
                <thead>
                    <th>Product Name</th>
                    <th>Description</th>
                    <th>Image</th>
                    <th>Price</th>
                    <th>Action</th>
                </thead>
                <tbody>
                    <tr v-for="pro in products" :key="pro.id">
                            <td>{{ pro.name }}</td>
                            <td>{{ pro.description }}</td>
                            <td>{{ pro.image }}</td>
                            <td>{{ pro.price }}</td>
                            <td class="text-center d-flex">
                                <inertia-link :href="`/product/${pro.id}`" class="btn btn-sm btn-primary me-2">Detail </inertia-link>
                                <inertia-link :href="`/product/${pro.id}/edit`" class="btn btn-sm btn-warning me-2">Edit </inertia-link>
                                <button @click.prevent="deleteProduct(`${pro.id}`)" class="btn btn-sm btn-danger">Del </button>
                            </td>
                        </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
    import LayoutApp from '../../Layouts/App.vue'
    import { Link } from '@inertiajs/inertia-vue3';
    import { Inertia } from '@inertiajs/inertia'

    export default {
        layout: LayoutApp,
        components: {
            Link
        },

        props: {
            products: Array
        },

        setup() {

            function deleteProduct(id) {
                if(confirm('Are you sure?'))
                Inertia.delete(`/product/${id}`)

            }

            return {
                deleteProduct
            }

        }

    }
</script>

<style>
    .card-header{
        background-color: #E9ECEF;
    }
</style>
