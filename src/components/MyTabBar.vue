<template>
  <div class="my-tab-bar">
    <div class="tab-item" v-for="(item,index) in itemList" :key="index" @click="tap(index)"
         :class="{current:index===current}">
      <!-- 图标 -->
      <span class="iconfont" :class="item.icon"></span>
      <!-- 文字 -->
      <span>{{ item.title }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyTabBar",
  props: {
    itemList: {
      type: Array,
      required: true,
      validator(value) {
        if (value?.length >= 2 && value?.length <= 5) {
          return true
        } else {
          throw RangeError("长度应该是2-5")
        }
      }
    },
  },
  data() {
    return {
      current: 0,
    }
  },
  methods: {
    tap(index) {
      this.current = index
      this.$emit("onTap", index)
    }
  },
}
</script>

<style lang="less" scoped>
.my-tab-bar {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 50px;
  border-top: 1px solid #ccc;
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: white;

  .tab-item {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}

.current {
  color: #1d7bff;
}
</style>