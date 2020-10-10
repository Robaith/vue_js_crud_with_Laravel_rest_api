<template>
  <div id="app">
    <div class="ui fixed inverted menu vue-color">
      <div class="ui container">
        <a href="#" class="header item">Vue js crud with laravel api</a>
      </div>
    </div>

    <div class="ui main container">
      <MyForm />
      <CustomerList :customers="customers" />
    </div>

  </div>
</template>
 
<script>
import axios from "axios";
import MyForm from "./components/MyForm";
import CustomerList from "./components/CustomerList";

export default {
  name: 'App',
  components: {
    MyForm,
    CustomerList
  },
  data() {
    return {
      url: "http://localhost/laravel-rest-api-master/public/api/customers",
      customers: []
    };
  },
  methods: {
    getCustomers() {
      axios.get(this.url).then(data => {
        this.customers = data.data;
      });
    }
  },
  created() {
    this.getCustomers();
  }

}
</script>

<style>
.vue-color{
  background: cyan !important;
}
.main.container{
  margin-top: 60px;
}
.submit-button{
  margin-top: 24px !important;
  float: right;
}
</style>
