<template>
    <div v-if="data" class="grid-container">
        <div class="customer">
            <h3>{{data.customer.givenName}} {{data.customer.familyName1}}</h3>
            <p>Phone: {{data.customer.phone}}</p>
            <p>{{data.customer.docType}}: {{data.customer.docNum}}</p>
        </div>

        <div class="products" v-if="data" v-for="product in data.products">
            <h3>{{product.name}}</h3>
            <p>Type: {{product.type}}</p>
            <p>Num: {{product.numeracioTerminal}}</p>
            <p>Sold at: {{product.soldAt}}</p>
        </div>
    </div>
</template>

<script lang="ts">

    export default {
        name:'CustomerDetail',
        props: {
            data: Object
        }
    };
</script>

<style scoped>
    div {
        margin: auto;
    }

    /*.card {*/
    /*    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);*/
    /*    max-width: 800px;*/
    /*    margin: auto;*/
    /*    text-align: center;*/
    /*}*/
    /*.card-product {*/
    /*    border: #2c3e50;*/
    /*    max-width: 800px;*/
    /*    margin: auto;*/
    /*    text-align: center;*/
    /*}*/

    .grid-container {
        display: grid;
        grid-template-columns: auto auto auto auto;
    }
</style>