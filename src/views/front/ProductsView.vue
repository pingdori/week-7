<template>
    這是產品列表頁面
    <table class="table">
        <tbody>
        <tr v-for="product in products" :key="product.id">
            <td>{{ product.title }}</td>
            <td><img :src="product.imageUrl" width="200" alt=""></td>
            <td></td>
            <RouterLink :to="`/product/${product.id}`"
            class="btn btn-outline-secondary">產品細節</RouterLink>
            <addToCart :id="product.id"></addToCart>
        </tr>
    </tbody>
    </table>
</template>
<script >
import { RouterLink } from 'vue-router'
import addToCart from '../../../../week-7/src/components/AddToCart.vue'
const { VITE_APP_URL, VITE_APP_PATH } = import.meta.env
// const一定要放在import後
export default {
  data () {
    return {
      products: []
    }
  },
  components: {
    RouterLink,
    addToCart
  },
  methods: {
    getProducts () {
      this.$http.get(`${VITE_APP_URL}/v2/api/${VITE_APP_PATH}/products/all`)
        .then((res) => {
          console.log(res)
          this.products = res.data.products
        })
    }
  },
  mounted () {
    this.getProducts()
  }
}
</script>
