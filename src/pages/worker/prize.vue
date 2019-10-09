<template>
  <div class="prize">
    <!-- 头部公共搜索框 -->
    <tabbar title="奖金兑换"></tabbar>
    <div class="content">
      <van-tabs v-model="active">
        <van-tab title="待兑换" class="duihuan">
          <div class="flex kuai">
            <div class="tu">
              <van-image
                width="3.5rem"
                height="3.5rem"
                fit="cover"
                src="https://img.yzcdn.cn/vant/cat.jpeg"
                radius="8"
              />
              <p>商品名字奥术大师大所大所</p>
              <p></p>
              <van-button type="primary" size="mini" color="#fc4c4c" @click="exchange">兑换</van-button>
            </div>
            <div class="tu">
              <van-image
                width="3.5rem"
                height="3.5rem"
                fit="cover"
                src="https://img.yzcdn.cn/vant/cat.jpeg"
                radius="8"
              />
              <p>商品名字</p>
              <van-button type="primary" size="mini" color="#fc4c4c" @click="exchange">兑换</van-button>
            </div>
          </div>
        </van-tab>
        <van-tab title="已兑换" class="duihuan">
          <div class="flex kuai">
            <div class="tu">
              <van-image
                width="3.5rem"
                height="3.5rem"
                fit="cover"
                src="https://img.yzcdn.cn/vant/cat.jpeg"
                radius="8"
              />
              <p>商品名字</p>
              <h4>已兑换</h4>
            </div>
            <div class="tu">
              <van-image
                width="3.5rem"
                height="3.5rem"
                fit="cover"
                src="https://img.yzcdn.cn/vant/cat.jpeg"
                radius="8"
              />
              <p>商品名字</p>
              <h4>已兑换</h4>
            </div>
          </div>
        </van-tab>
        <van-tab title="已打款" class="duihuan">
          <div class="flex kuai">
            <div class="tu">
              <van-image
                width="3.5rem"
                height="3.5rem"
                fit="cover"
                src="https://img.yzcdn.cn/vant/cat.jpeg"
                radius="8"
              />
              <p>商品名字</p>
              <h4>已付款</h4>
            </div>
            <div class="tu">
              <van-image
                width="3.5rem"
                height="3.5rem"
                fit="cover"
                src="https://img.yzcdn.cn/vant/cat.jpeg"
                radius="8"
              />
              <p>商品名字</p>
              <h4>已付款</h4>
            </div>
          </div>
        </van-tab>
        <van-tab title="已完成" class="duihuan">
          <div class="flex kuai">
            <div class="tu">
              <van-image
                width="3.5rem"
                height="3.5rem"
                fit="cover"
                src="https://img.yzcdn.cn/vant/cat.jpeg"
                radius="8"
              />
              <p>商品名字</p>
              <h4>已完成</h4>
            </div>
            <div class="tu">
              <van-image
                width="3.5rem"
                height="3.5rem"
                fit="cover"
                src="https://img.yzcdn.cn/vant/cat.jpeg"
                radius="8"
              />
              <p>商品名字</p>
              <h4>已完成</h4>
            </div>
          </div>
        </van-tab>
        <van-tab title="已拒绝" class="duihuan">
          <div class="flex kuai">
            <div class="tu">
              <van-image
                width="3.5rem"
                height="3.5rem"
                fit="cover"
                src="https://img.yzcdn.cn/vant/cat.jpeg"
                radius="8"
              />
              <p>商品名字</p>
              <h4>已拒绝</h4>
            </div>
            <div class="tu">
              <van-image
                width="3.5rem"
                height="3.5rem"
                fit="cover"
                src="https://img.yzcdn.cn/vant/cat.jpeg"
                radius="8"
              />
              <p>商品名字</p>
              <h4>已拒绝</h4>
            </div>
          </div>
        </van-tab>
      </van-tabs>
    </div>
  </div>
</template>
<script>
import tabbar from "../../components/navbar";
export default {
  data() {
    return {
      active: "1"
    };
  },
  components: {
    tabbar
  },
  mounted() {
    this.type = this.$route.query.type;
  },
  methods: {
    exchange() {
      this.$toast("兑换成功");
    }
  }
};
</script>

<style lang="less" scoped>
.prize {
  padding-top: 44px;
  .content {
    .duihuan {
      padding: 10px;
    }
    .kuai {
      margin: 5px 0;
    }
    .tu {
      border-radius: 10px;
      padding: 20px;
      box-shadow: 1px 3px 5px #e6dada;
      .van-button--mini {
        margin-top: 10px;
      }
      h4 {
        color: #fc4c4c;
      }
      p {
        width: 100px;
        overflow: hidden;
        text-overflow: ellipsis; //超出部分以省略号显示
        white-space: nowrap;
        font-size: 16px;
      }
    }
  }
}
</style>
