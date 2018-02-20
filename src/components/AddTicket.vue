<template>
  <div class="container">
    <h1>Create A Ticket</h1>
    <form v-on:submit.prevent="addTicket">
      <div class="row">
        <div class="col-md-6">
          <div class="form-group">
            <label>Email ID:</label>
            <input type="text" class="form-control" v-model="ticket.email"/>
          </div>
        </div>
        </div>
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <label>Ticket Description:</label>
              <textarea cols="5" rows="5" class="form-control col-md-6" v-model="ticket.description"></textarea>
            </div>
          </div>
        </div><br />
        <div class="form-group">
          <button class="btn btn-primary">Create Ticket</button>
        </div>
    </form>
  </div>
</template>
<script>
export default {
    data(){
        return {
          ticket: {}
        }
    },
    methods: {
       addTicket() {
             let uri = 'http://localhost:4000/tickets/add';
            this.axios.post(uri, this.ticket).then((response) => {
               console.log(response);
            });
       }
    }
}
</script>