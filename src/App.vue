<template>
  <div id="app">
    <my-header title="导航栏"/>
    <component :is="name"></component>
    <my-tab-bar :item-list="itemList" @onTap="updateContent"></my-tab-bar>
  </div>
</template>

<script>

import MyHeader from "@/components/MyHeader";
import MyTabBar from "@/components/MyTabBar";
import MyGoodsList from "@/view/MyGoodsList";
import MyUserInfo from "@/view/MyUserInfo";
import MyGoodsSearch from "@/view/MyGoodsSearch";

export default {
  name: 'App',
  components: {
    MyGoodsSearch,
    MyUserInfo,
    MyGoodsList,
    MyTabBar,
    MyHeader,
  },
  data() {
    return {
      name: "MyGoodsList",
      itemList: [
        {
          icon: "icon-shangpinliebiao", title: "列表", name: "MyGoodsList",
        },
        {
          icon: "icon-sousuo", title: "搜索", name: "MyGoodsSearch",
        },
        {
          icon: "icon-user", title: "我的", name: "MyUserInfo",
        },
      ],
    }
  },
  methods: {
    updateContent(index) {
      this.name = this.itemList[index].name
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
