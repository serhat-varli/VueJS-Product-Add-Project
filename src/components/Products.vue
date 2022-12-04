<template>
    <div v-if="(productList.length > 0)">
        <h3 class="text-center">Product List</h3>
        <hr />
        <div class="row product-container">
            <Products v-for="product in productList">
                <img class="card-img-top" :src="product.selectedImage" :alt="product.title">
                <div class="card-body">
                    <h5 class="card-title">{{ product.title }}</h5>
                    <small>
                        <strong>Count : </strong> {{ product.count }}
                    </small>
                    <br>
                    <small>
                        <strong>Price : </strong> {{ product.price }}
                    </small>
                    <br>
                    <small>
                        <strong>Amount : </strong> {{ product.totalPrice }}
                    </small>
                </div>

            </Products>
        </div>
    </div>


</template>

<script>
import { eventBus } from '../main';
import Products from './Product.vue'
export default {
    components: {
        Products
    },
    data() {
        return {
            productList: []
        }
    },
    created() {
        eventBus.$on("productAdded", (item) => {
            if (this.productList.length <= 9) {
                this.productList.push(item)
                eventBus.$emit("progressUpdate", this.productList.length);
            }
            else {
                alert("Daha fazla ürün ekleyemezsiniz!")
            }
        })
    }
}
</script>