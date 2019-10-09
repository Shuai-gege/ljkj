<template>
  <div class="home">
    <!-- 搜索 -->
    <search url="/search"></search>
    <!-- 中间 -->
    <div class="Center">
      <!-- 下拉刷新 -->
      <van-pull-refresh v-model="isLoading" @refresh="onRefresh">
        <!-- 轮播图 -->
        <van-swipe
          :autoplay="3000"
          indicator-color="white"
          :height="200"
          class="Lunbo"
          style="border-radius:15px"
        >
          <van-swipe-item class="lun" v-for="(item,i) in lunbo" :key="i">
            <van-image width="750" height="200" fit="cover" :src="item" />
          </van-swipe-item>
        </van-swipe>
        <!-- 分类 -->
        <!-- <van-grid :gutter="10" style="border-radius:15px">
          <van-grid-item v-for="value in 8" :key="value" icon="photo-o" text="这是啥" />
        </van-grid>-->
        <!-- tap商品 -->
        <!-- <van-tabs v-model="active" animated>
          <van-tab title="每日推荐">
            <list :list="list"></list>
          </van-tab>
          <van-tab title="每日精选">
            <list :list="list"></list>
          </van-tab>
        </van-tabs>-->
        <list :list="list"></list>
      </van-pull-refresh>
    </div>
  </div>
</template>

<script>
import search from "@/components/com-search";
import list from "@/components/com-list";
export default {
  components: {
    search,
    list
  },
  data() {
    return {
      isLoading: false,
      // active: 0,
      lunbo: [],
      list: []
    };
  },
  mounted() {
    if (!localStorage.getItem("token") && !this.$route.query.token) {
      alert(33333333);
      location.href = "http://lj.tieqiao.shop/api/user/wxlogin";
    } else if (!localStorage.getItem("token") && this.$route.query.token) {
      alert(11111111111);
      localStorage.setItem("token", this.$route.query.token);
      this.init();
    } else if (localStorage.getItem("token")) {
      this.init();
    }
  },
  methods: {
    init() {
      this.axios.post("/api/index/index").then(data => {
        this.lunbo = data.index_banner.split(",");
        this.list = data.good_list;
      });
    },
    onRefresh() {
      setTimeout(() => {
        this.$toast("好看吗？");
        this.isLoading = false;
      }, 500);
    }
  }
};
</script>

<style scoped lang="less">
.home {
  .van-row {
    margin-bottom: 15px;
    margin-top: -15px;
  }
}

.lun {
  background: rgba(51, 119, 255, 0.5);
}

.van-grid {
  // background: rgba(51, 119, 255, 0.5);
}

.van-search {
  position: fixed;
  width: 100%;
  z-index: 100;
}

.Lunbo {
  margin: 70px 20px 20px;
}

.swipe {
  margin: 0 auto;
}

.Center {
  //   padding-top: 55px;
  margin-bottom: 50px;
}

.van-col--offset-1 {
  margin-top: -2.625rem;
}

.Zi {
  color: #f00;
}
.list {
  padding: 12px;
  flex-wrap: wrap;
  margin-top: -1px;
  li {
    width: 48%;
    margin-bottom: 10px;
    box-shadow: 1px 3px 5px #e6dada;
    border-radius: 5px;

    .name {
      font-size: 15px;
      margin: 10px 5px 5px;
      color: #333;
    }
    .pro {
      font-size: 12px;
      color: #666;
      margin: 0 5px;
    }
    .price {
      font-size: 20px;
      color: #f00;
      margin: 5px;
      i {
        font-size: 10px;
      }
    }
  }
}
header {
  height: 44px;
}
</style>
