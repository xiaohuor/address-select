<template>
  <div>
    <Select :disabled="disabled" v-model="provinceCode" placeholder="省份" style="width:49%;float:left">
      <Option v-for="item in provinceList" :value="item.id" :key="item.id">{{ item.name }}</Option>
    </Select>
    <Select :disabled="disabled" v-model="cityCode" placeholder="城市" style="width:49%;float:right">
      <Option v-for="item in cityList" :value="item.id" :key="item.id">{{ item.name }}</Option>
    </Select>
  </div>
</template>

<script>
import prodata from "./provinceCity.js";
import { setTimeout } from "timers";
export default {
  name: "province-city",
  props: ["proCode", "ciCode","disabled"],
  watch: {
    disabled(val){

    },
    proCode(code) {
      
      this.provinceCode = +code;
    },
    ciCode(code) {
      this.cityCode = +code;
    },
    provinceCode(code) {
      this.$emit("getProvinceCode", code);
      prodata.forEach(item => {
        if (item.id == code) {
          this.cityList = item["citys"];
          this.$nextTick(() => {
            this.cityCode = this.ciCode;
          });
        }
      });
    },
    cityCode(code) {
      this.$emit("getCityCode", code);
    }
  },
  created() {},
  mounted() {
    var that = this;
    this.provinceList = prodata;
    console.log("组件传过来的值", this.proCode);
    setTimeout(() => {
      that.provinceCode = that.proCode;
    }, 2000);
  },
  data() {
    return {
      provinceCode: "",
      cityCode: "",
      provinceList: [],
      cityList: []
    };
  },
  methods: {}
};
</script>

<style >
</style>