<template>
  <div class="audit">
    <navbar title="审核授权"></navbar>
    <div class="content">
      <div
        class="flex box"
        v-for="(item,index) in list"
        :key="index"
        @click="tap(item.invite_agent_id)"
      >
        <div class="flex_l">
          <img :src="item.wx_avatar" alt />
          <div>
            <p style="color:black;font-size:16px;">{{item.wx_nickname}}</p>
            <p>申请级别：{{item.level_name}}</p>
          </div>
        </div>
        <div>
          {{item.createtime}}
          <br />
          <span style="color:#fc4c4c" v-if="item.man_check_status==1">未审核</span>
          <span style="color:#fc4c4c" v-if="item.man_check_status==2">审核通过</span>
          <span style="color:#fc4c4c" v-if="item.man_check_status==3">审核失败</span>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import navbar from "@/components/navbar";
export default {
  data() {
    return {
      page: "1",
      infodata: {},
      list: [],
      audit: "" //审核状态
    };
  },
  methods: {
    tap(id) {
      this.$router.push({
        path: "/auditcontent",
        query: {
          id: id
        }
      });
    }
  },
  components: {
    navbar
  },
  mounted() {
    this.axios
      .post("/api/agent/agentEmpower", { page: this.page })
      .then(data => {
        this.list = data;
      });
  }
};
</script>
<style lang="less" scoped>
.audit {
  font-size: 14px;
  .content {
    margin-top: 44px;
    .box {
      width: 94%;
      padding: 10px 0;
      margin: 0 auto 10px;
      border-bottom: 1px solid #cecece;
    }
    img {
      width: 60px;
      height: 60px;
      border-radius: 7px;
      margin-right: 10px;
    }
  }
}
</style>