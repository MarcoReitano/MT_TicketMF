<template>
  <div class="ticketelementcontainer box">
    <div>{{ticket.category}}</div>
    <div>{{ticket.price}}€</div>
    <div v-if="ticket.available !== 'available'">Sold out!</div>
    <div v-else>
      <order-add-cart-button></order-add-cart-button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'TicketElement',
    props: {
      ticket: Object
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import url("https://cdnjs.cloudflare.com/ajax/libs/bulma/0.7.5/css/bulma.min.css") screen;
</style>
