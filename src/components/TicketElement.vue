<template>
  <div class="ticketelementcontainer">
    <p>{{ticket.category}}</p>
    <p>{{ticket.price}}</p>
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
  h3 {
    margin: 40px 0 0;
  }
</style>
