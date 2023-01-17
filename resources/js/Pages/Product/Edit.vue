<template>
    <div class="card">
        <div class="card-header">
            <h5>Add Product</h5>
        </div>
        <div class="card-body">
            <form @submit.prevent="update">
                <div class="mb-3">
                    <label for="name" class="form-label">Product Name</label>
                    <input type="text" v-model="product.name" class="form-control" id="name" placeholder="">
                    <div v-if="errors.name">
                        <p class="text-danger">{{ errors.name }}</p>
                    </div>
                </div>
                <div class="mb-3">
                    <label for="description" class="form-label">Description</label>
                    <input type="text" v-model="product.description" class="form-control" id="description" placeholder="">
                    <div v-if="errors.description" class="mt-1">
                        <p class="text-danger">{{ errors.description }}</p>
                    </div>
                </div>
                <div class="mb-3">
                    <label for="price" class="form-label">Price</label>
                    <input type="text" v-model="product.price" class="form-control" id="price" placeholder="">
                    <div v-if="errors.price" class="mt-1">
                        <p class="text-danger">{{ errors.price }}</p>
                    </div>
                </div>
                <div class="mb-3">
                    <button type="submit" class="btn btn-primary btn-md shadow-sm me-2">Submit</button>
                    <button type="reset" class="btn btn-warning btn-md shadow-sm me-2">Reset</button>
                    <inertia-link href="/" class="btn btn-secondary btn-md shadow-sm">Back</inertia-link>
                </div>
                
            </form>
        </div>
    </div>
</template>

<script>
    import LayoutApp from '../../Layouts/App.vue'
    import { reactive } from 'vue'
    import { Inertia } from '@inertiajs/inertia'

    export default {
        layout: LayoutApp,

        props: {
            product: Object,
            errors: Object
        },

        setup(props) {

            const product = reactive({
                name: props.product.name,
                description: props.product.description,
                price: props.product.price,
            })

            function update() {
                
                let name   = product.name
                let description   = product.description
                let price   = product.price

                //send data
                Inertia.put(`/product/${props.product.id}`, {
                    name: name,
                    description: description,
                    price: price,
                })
             
            }

            return {
                product,
                update
            }

        }
    }
</script>