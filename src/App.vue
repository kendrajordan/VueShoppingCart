<template>
<div class="container">
  <div class="row">
    <!-- List of products-->
    <div class="col-md-7">
      <div class="row">
        <div class="col-md-6" v-for="product in products" v-bind:key= "product.id">
          <product v-bind:isInCart="isInCart(product)" v-on:add-to-cart="addToCart(product)"v-bind:product="product"></product>
        </div>
      </div>
    </div>
    <!--Shopping Cart -->
    <div class="col-md-5">
      <cart v-bind:items="cart"v-on:remove-from-cart="RemoveFromCart($event)" v-on:pay="pay()"></cart>
    </div>
  </div>
</div>
</template>

<script>
//import the array of products from products.json file
import products from '@/products.json';
//import product component
import Product from '@/components/Product.vue';
//import cart component
import Cart from '@/components/Cart.vue';


export default {
  name: 'app',
  components:{
    Product,
    Cart
  },
  data(){

    return{
      products,

      cart:[]
    }
  },
  methods:{

    addToCart(product){

      this.cart.push(product);
    },
    isInCart(product){
      const item = this.cart.find(item =>item.id === product.id);
      if(item){
        return true;
      }else{
        return false;
      }
    },
    RemoveFromCart(product){
      this.cart = this.cart.filter(item =>item.id !== product.id)
    },
    pay(){

      this.cart = [];
      alert("Shopping completed !")
    }
  }
}
</script>
<!-- If you only want to apply styling to a single component, the you will need <table>
  to scope it. <style scoped>
>-->
<style>
  body{
    background-color: #FBF8F3 !important;
  }
</style>
