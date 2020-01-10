<template>
  <div class="products">
    <div v-for="(product,i) in products" :key="i" class="product">
      <div class="product__infos">
        <div class="product__imgWrapper" >
          <img class="product__img" :src="product.pictures[0]" alt="">
        </div>
        <div class="product__name" >{{product.name}}</div>
        <div class="product__name" >{{}}</div>
        <div class="product__name" >{{}}</div>
      </div>

    </div>
  </div>
</template>

<script>
  import {mapActions, mapState} from 'vuex'

  export default {
    name: "products",
    mounted() {
      this.fetchProducts()
    },
    computed: mapState({products: state => state.products}),
    methods: {
      ...mapActions(['fetchProducts'])
    }
  }
</script>

<style scoped>

</style>
