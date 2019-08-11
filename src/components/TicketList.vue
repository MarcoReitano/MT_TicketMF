<template>
  <div class="hello">
    <ticket-element v-for="ticket of tickets" v-bind:key="concert.date"
                    v-bind:ticket="ticket"></ticket-element>
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

    data: function () {
      return {
        resultData: '',
        concerts: ''
      }
    },

    created() {
      getTickets();
    },

    getTickets() {
      axios.get(`https://api.marcoreitano.dev/tickets/search/findByConcert`, {
        params: {
          concerturi: this.concerturi
        }
      })
      .then(response => {
        console.log(response);
      })
      .catch(error => {
        console.log(error);
      });
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h3 {
    margin: 40px 0 0;
  }
</style>
