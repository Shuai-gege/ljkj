<template>
  <div class="box">
    <div class="head flex">
      <van-button type="primary" @click="showPopup" icon="bars" class="geren"></van-button>
      <div class="search">
        <input class="sear" placeholder="请输入搜索关键字" @focus="tosearch" />
        <van-icon name="search" />
      </div>
      <div class="text">取消</div>
    </div>
    <van-popup v-model="show" position="left" :style="{ height: '100%' ,width:'50%'}">
      <!-- 头像 -->
      <div class="logo center">
        <van-image fit="cover" width="2.5rem" height="2.5rem" radius="13" :src="info.wx_avatar" />
        <p style="font-size:16px;color:black">
          {{info.wx_nickname}}
          <van-tag round color="#fc4c4c">{{info.agent_name}}</van-tag>
        </p>
      </div>
      <van-divider />
      <!-- 设置 -->
      <van-cell title="我的" icon="manager-o" to="/my" />
      <van-cell title="信息" icon="chat-o" to="/message" />
      <van-cell title="购物车" icon="cart-o" to="/car" />
      <!-- 信息，购物车 -->
    </van-popup>
    <!-- 搜索框 -->
  </div>
</template>
<script>
export default {
  data() {
    return {
      show: false,
      info: {} //个人信息
    };
  },
  props: ["url"],
  mounted() {
    this.axios.post("/api/user/index").then(data => {
      console.log(data);
      this.info = data;
    });
  },
  methods: {
    tosearch() {
      this.$router.push(this.url);
    },
    showPopup() {
      this.show = true;
    }
  }
};
</script>
<style lang="less" scoped>
.Tou {
  position: fixed;
  z-index: 100;
  width: 100%;
}

.geren {
  height: 54px;
}

.txt {
  font-size: 12px;
}

.logo {
  text-align: center;
  margin-top: 1rem;
  flex-direction: column;
}
.van-image--round {
  width: 100px;
  height: 100px;
}
.logo p {
  font-size: 12px;
  margin-top: 10px;
}

.bian {
  border-bottom: 1px solid #ccc;
}

.van-button--primary {
  background: #90d7ec;
  border: 1px solid #90d7ec;
}
.head {
  background-color: #90d7ec;
  padding: 0 20px 0 0;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 99;
}
.search {
  flex: 1;
  margin: 0 15px;
  background-color: #fff;
  border-radius: 20px;
  height: 30px;
  position: relative;
  .sear {
    border: none;
    width: 85%;
    height: 100%;
    border-radius: 20px;
    padding-left: 15%;
  }
  i {
    position: absolute;
    left: 15px;
    top: 10px;
  }
}
</style>