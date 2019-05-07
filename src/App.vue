<template>
  <div id="app">
    <Form :label-width="100">
      <FormItem label="省份/地市">
        <AddressSelect :width="400" @setCity="setCity"/>
      </FormItem>
      <FormItem label="省份/地市">
        <AddressSelect :width="400" @setCity="setCity" :provinceId="130000" :cityId="130300"/>
      </FormItem>
    </Form>
  </div>
</template>

<script>
import AddressSelect from "./components/address-select";

export default {
  name: "app",
  components: {
    AddressSelect
  },
  data() {
    return {
      city: {},
    }
  },
  methods: {
    setCity(city) {
      this.city = city;
    }
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
