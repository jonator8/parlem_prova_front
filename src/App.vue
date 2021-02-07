<template>
  <img alt="Vue logo" src="./assets/logo.png" />
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
