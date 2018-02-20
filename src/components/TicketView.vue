<template>
    <div class="container">
        <h1>Tickets</h1>
        <table class="table table-hover">
            <thead>
            <tr>
                <td>ID</td>
                <td>Email ID</td>
                <td>Description</td>
            </tr>
            </thead>
            <tbody>
               <tr v-for="ticket in tickets" :key="ticket._id">
                    <td>{{ ticket._id }}</td>
                    <td>{{ ticket.email }}</td>
                    <td>{{ ticket.description }}</td>
                    <td></td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>

    export default {
        data(){
            return{
                tickets: []
            }
        },

        created: function()
        {
            this.fetchItems();
        },

        methods: {
            fetchItems()
            {
              let uri = 'http://localhost:4000/tickets';
              this.axios.get(uri).then((response) => {
                  this.tickets = response.data;
              });
            }
        }
    }
</script>