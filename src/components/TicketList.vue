<template>
  <div class="ticketlistcontainer">
    TicketList
    <ticket-element v-for="ticket in tickets" v-bind:key="ticket.id"
                    :ticketuri="ticket._links.self.href"
                    :available="ticket.availability"></ticket-element>
  </div>
</template>

<script>
  import TicketElement from "./TicketElement";
  import axios from "axios";

  export default {
    name: 'TicketList',
    components: {TicketElement},
    props: {
      concerturi: String
    },
    config: {
      ignoredElements: [
        'order-add-cart-button'
      ]
    },
    data: function () {
      return {
        tickets: []
      }
    },
    mounted: function () {
      console.log("Mounted");
      this.getTickets();
    },
    watch: {
      concerturi: function (newVal) { // watch it
        if (newVal) {
          this.getTickets();
        }
      }
    },
    methods:
        {
          getTickets: function () {
            axios.get(`https://api.marcoreitano.dev/tickets/search/findByConcert`, {
              params: {
                concerturi: this.concerturi
              }
            })
            .then(response => {
              this.tickets = response.data._embedded.tickets;
              console.log(this.tickets);
            })
            .catch(error => {
              console.log(error);
            });
          }
        }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import url("https://cdnjs.cloudflare.com/ajax/libs/bulma/0.7.5/css/bulma.min.css") screen;
</style>
