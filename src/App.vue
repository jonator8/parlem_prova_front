<template>
  <img alt="Vue logo" src="./assets/parlem.png" />
  <CustomerList />
</template>

<script>
import CustomerList from './components/CustomerList.vue'

export default {
  name: 'App',
  components: {
    CustomerList
  }
}
</script>
