<template>
    <div class="list row">
        <div class="col-md-6">
            <h3>Customers</h3>
            <table>
                <thead>
                <tr>
                    <th>Id</th>
                    <th>Name</th>
                    <th>Last</th>
                    <th>Phone</th>
                </tr>
                </thead>
                <tbody>
                <tr v-for="customer in customers">
                    <td>{{customer.id}}</td>
                    <td>{{customer.givenName}}</td>
                    <td>{{customer.familyName1}}</td>
                    <td>{{customer.phone}}</td>
                </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script lang="ts">
    import axios from "axios";


    export default {
        name:'CustomerList',

        data () {
            return {
                customers: null
            }
        },

        created() {
            axios.get("http://localhost:3000/api/v1/customers").then((result) => {
                this.customers = result.data.data;
            })
        },
    };
</script>

<style>
    table {
        margin: auto;
    }

    th, td {
        border-bottom: 1px solid #ddd;
        padding: 15px;
        text-align: left;
    }

    tr:hover {background-color: #f5f5f5;}
</style>