<template>
<div class="card my-5">
  <div class="card-body">
    <h5 class="text-center card-title">{{product.title}}</h5>
    <p class="text-center text-muted card-text display-4">${{Number(product.price).toFixed()}}</p>
    <button v-bind:disabled="isInCart" class="btn btn-primary form-control" v-on:click="$emit('add-to-cart',product)">{{isInCart ? 'Added to Cart':'Add To Cart'}}</button>

  </div>
</div>

</template>
<script>
  export default{
    props:['product','isInCart']
  }
</script>
<style scoped>

</style>
