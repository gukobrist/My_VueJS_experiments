<template>
  <div>
    <my-header></my-header>
    <h1>Это айди товара {{ $route.params.id }}</h1>
    <div class="row">
      <div class="col-md-5 col-md-offset-0">
        <figure>
          <img class="product" v-bind:src="product.image">
        </figure>
      </div>
      <div class="col-md-6 col-md-offset-0 description">
        <h1> {{ product.title }}</h1>
        <p v-html="product.description"></p>
        <p class="price">
          {{ product.price }}
        </p>
        <button @click="edit">Редактировать дилду</button>
        <router-view></router-view>
      </div>
    </div>
  </div>
</template>

<script>
import MyHeader from "./Header";
export default {
  name: "Product",
  components: {MyHeader},
  data() {
    return {
      product: ''
    }
  },
  methods: {
    edit() {
      this.$router.push({name: 'Edit'})
    }
  },
  created() {
    axios.get('/static/products.json')
      .then((response) => {
      this.product = response.data.products.filter(
        data => data.id == this.$route.params.id)[0]
      this.product.image = '/' + this.product.image;
      });
  }
}
</script>

<style scoped>

</style>
