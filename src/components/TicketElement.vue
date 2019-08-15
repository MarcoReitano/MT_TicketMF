<template>
  <div class="ticketelementcontainer box">
    <div>{{ticket.category}}</div>
    <div>{{ticket.price}}€</div>
    <div v-if="ticket.availability !== 'available'">
      <button class="button is-primary" disabled>
        <span class="icon">
          <i class="fa fa-cart-plus"></i>
        </span>
        <span>Sold out!</span>
      </button>
    </div>
    <div v-else>
      <order-add-cart-button ticketuri={{this.ticket._links.self.href}}
                             available={{this.ticket.availability}}></order-add-cart-button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'TicketElement',
    props: {
      ticket: Object
    },
    config: {
      ignoredElements: [
        'order-add-cart-button'
      ]
    },
    mounted: function () {
      console.log(this.ticket.availability);
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import url("https://cdnjs.cloudflare.com/ajax/libs/bulma/0.7.5/css/bulma.min.css") screen;
</style>
