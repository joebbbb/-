<template>

    <el-pagination
      background
      layout="prev, pager, next"
      @current-change="handleCurrentChange"
      :page-size="msg.pageSize"
      :current-page="msg.page"
      :page-count="msg.total"
      :total="msg.total"
     >
    </el-pagination>

</template>

<script>
  export default {
    name: "pagination",
    props: ["msg"],
    methods: {
      handleCurrentChange(val) {
        this.$emit('refreshList',val);
      },
    }
  }
</script>

<style scoped>

  /*.page{*/
    /*text-align: right;*/
    /*margin: 20px auto 20px;*/
  /*}*/
</style>
