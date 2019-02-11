<template>
  <div>
    <ul class="list-group my-5">
      <li class="list-group-item" v-for="item in items" v-bind:key="item.id">

          {{item.title}} - ${{item.price}}
        <!--
        product name - $234
        button to remove the item from the cart
        -->
        <button class="btn badge badge-danger float-right" v-on:click="$emit('remove-from-cart',item)">Remove from Cart</button>
      </li>
    </ul>
    <div class="card p-3 p-3 my-5">
      <h4 class="text-center">${{total}}</h4>
    </div>

    <button v-bind:disabled="items.length === 0" class="btn btn-info form-control" v-on:click="$emit('pay')">Pay Now</button>
  </div>
</template>

<script>

  export default{

    props:['items'],
    computed:{
      total(){
        return this.items.reduce((acc, item) => acc + Number(item.price),0);
        }
      }

  }
</script>
