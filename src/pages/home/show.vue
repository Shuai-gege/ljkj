<template>
  <div class="show">
    <!-- 头部公共搜索框 -->
    <!-- <tabbar title="未授权"></tabbar> -->
    <div class="content" v-html="con" style="padding:12px;"></div>
  </div>
</template>
<script>
// import tabbar from "../../components/navbar";
export default {
  data() {
    return {
      con: ""
    };
  },

  mounted() {
    this.axios.post("/api/index/unauthorized").then(data => {
      console.log(data);
      this.con = data;
    });
  },
  methods: {}
};
</script>

<style lang="less" scoped>
.show {
  .content {
  }
}
</style>
