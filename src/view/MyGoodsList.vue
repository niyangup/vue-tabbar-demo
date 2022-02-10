<template>
  <div>
    <my-table :dataList="list">
      <template v-slot:header>
        <th>#</th>
        <th>商品名称</th>
        <th>价格</th>
        <th>标签</th>
        <th>操作</th>
      </template>
      <template #body="{row:item,index}">
        <td>{{ item.id }}</td>
        <td>{{ item.goods_name }}</td>
        <td>{{ item.goods_price }}</td>
        <td>
          <span class="badge bg-warning text-dark" v-for="(tagItem,index) in item.tags" :key="index">
            {{ tagItem }}
          </span>
        </td>
        <td>
          <button class="btn btn-danger" @click="deleteItem(index)">删除</button>
        </td>
      </template>
    </my-table>
  </div>
</template>

<script>
import MyTable from "@/components/MyTable";

export default {
  name: "MyGoodsList",
  components: {MyTable},
  data() {
    return {
      list: [],
    }
  },
  methods: {
    deleteItem(index) {
      console.log(index)
      this.list.splice(index, 1)
    }
  },
  created() {
    this.$axios.get("/api/goods").then(value => {
      console.log(value.data.data)
      this.list.push(...value.data.data)
    }).catch(reason => {
      console.log(reason)
    })
  }
}
</script>

<style scoped>

</style>