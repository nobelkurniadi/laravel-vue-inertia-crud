<template>
    <div class="card">
        <div class="card-header">
            <h5>Product Detail</h5>
        </div>
        <div class="card-body">
            <ul class="list-group">
                <li class="list-group-item">
                    <div class="row">
                        <div class="col-md-3">Product Name</div>
                        <div class="col-md-9">: {{ product.name }}</div>
                    </div>
                </li>
                <li class="list-group-item">
                    <div class="row">
                        <div class="col-md-3">Description</div>
                        <div class="col-md-9">: {{ product.description }}</div>
                    </div>
                </li>
                <li class="list-group-item">
                    <div class="row">
                        <div class="col-md-3">Image</div>
                        <div class="col-md-9">: {{ product.image }}</div>
                    </div>
                </li>
                <li class="list-group-item">
                    <div class="row">
                        <div class="col-md-3">Price</div>
                        <div class="col-md-9">: {{ product.price }}</div>
                    </div>
                </li>
                <li class="list-group-item">
                    <div class="row">
                        <div class="col-md-3"><inertia-link href="/" class="btn btn-secondary">Back</inertia-link></div>
                    </div>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
    import LayoutApp from '../../Layouts/App.vue'
    import { reactive } from 'vue'

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
                image: props.product.image,
                price: props.product.price,
            })

            return {
                product,
            }

        }
    }
</script>