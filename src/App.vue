<template>
  <div id="app">
    <my-header title="导航栏"/>
    <component :is="name" class="main"></component>
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

<style scoped lang="less">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  .main {
    margin-top: 45px;
    margin-bottom: 50px;
  }
}
</style>
