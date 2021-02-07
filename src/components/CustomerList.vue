<template>
    <div class="list row">
        <div class="col-md-6">
            <h3>Customers</h3>
            <table>
                <thead>
                <tr>
                    <th>Id</th>
                    <th>Name</th>
                    <th>Email</th>
                </tr>
                </thead>
                <tbody>
                <tr v-for="customer in customers"
                    @click="clickCustomer(customer)">
                    <td>{{customer.id}}</td>
                    <td>{{customer.givenName}}</td>
                    <td>{{customer.email}}</td>
                </tr>
                </tbody>
            </table>
        </div>
        <CustomerDetail v-bind:data="data"></CustomerDetail>
    </div>
</template>

<script lang="ts">
    import axios from "axios";
    import CustomerDetail from "./CustomerDetail.vue";


    export default {
        name:'CustomerList',
        components: {CustomerDetail},
        data () {
            return {
                customers: null,
                data: null
            }
        },
        methods: {
            clickCustomer(customer: any) {
                axios.get("http://localhost:3000/api/v1/customers/"+customer.id+"/products").then((result) => {
                    let dataAux = {
                        customer: result.data.data.customer,
                        products: []
                    };
                    result.data.data.products.map(item => {
                        const product = {
                            name: item.product.name,
                            type: item.product.type,
                            soldAt:  new Date(item.soldAt).toLocaleString(),
                            numeracioTerminal: item.numeracioTerminal
                        };
                        dataAux.products.push(product);
                    });
                    this.data = dataAux;
                });
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