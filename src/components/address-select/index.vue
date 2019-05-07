<template>
  <div :style="`width: ${width}px`">
    <Select v-model="province" placeholder="选择省份" style="width:40%;" @on-change="provinceChange">
      <Option v-for="(item, index) in provinceList" :value="index" :key="item.id">{{ item.name }}</Option>
    </Select>
    <Select v-model="city" placeholder="选择城市" style="width:40%;margin-left: 10px;" @on-change="cityChange">
      <Option v-for="(item, index) in cityList" :value="index" :key="item.id">{{ item.name }}</Option>
    </Select>
  </div>
</template>

<script>
import provinceCity from "./province-city"
export default {
  name: "AddressSelect",
  props: {
    width: {
      type: Number,
      default: 400
    },
    provinceId: {
      type: Number,
      default: null,
    },
    cityId: {
      type: Number,
      default: null,
    }
  },
  
  data() {
    return {
      province: null,
      city: null,
      provinceList: provinceCity,
      cityList: [],
    };
  },
  watch: {
    provinceId(val) {
      if(val) {
        this.provinceList.forEach((item, index)=>{
          if(item.id==val)
          this.province = index;
        })
      }
    }
  },
  created() {
    if(this.provinceId) {
      this.provinceList.forEach((item, index)=>{
        if(item.id==val)
        this.province = index;
      })
    }
  },
  methods: {
    provinceChange(index) {
      this.cityList = this.provinceList[index].citys;
    },
    cityChange(index) {
      this.$emit("setCity", this.cityList[index])
    },
  },
};
</script>

<style lang="scss" scoped>
</style>