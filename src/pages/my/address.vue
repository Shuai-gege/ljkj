<template>
  <div class="address">
    <tabbar title="收货地址" back="/my"></tabbar>
    <div class="null" v-if="list.length==0">暂无地址</div>
    <van-address-list
      class="list"
      v-model="chosenAddressId"
      @select="getAdd"
      :list="list"
      @add="onAdd"
      @edit="onEdit"
    />
  </div>
</template>
<script>
import tabbar from "../../components/navbar";
export default {
  components: {
    tabbar
  },
  data() {
    return {
      chosenAddressId: "",
      list: []
    };
  },
  mounted() {
    this.init();
  },
  methods: {
    init() {
      this.axios.post("/api/address/index").then(data => {
        data.forEach(item => {
          this.$set(item, "tel", item.phone);
          this.$set(item, "id", item.address_id);
          this.$set(
            item,
            "address",
            item.province_name +
              " " +
              item.city_name +
              " " +
              item.district_name +
              " " +
              item.details
          );
          if (item.status == 1) {
            this.chosenAddressId = item.address_id;
          }
        });
        this.list = data;
      });
    },
    onAdd() {
      this.$router.push("/add_address");
    },
    onEdit(item, index) {
      this.$router.push({
        path: "/edit_address",
        query: { id: item.id }
      });
    },
    getAdd(item) {
      console.log(item.id); //选中的地址id
      console.log(this.chosenAddressId);
    }
  }
};
</script>
<style lang="less">
.list {
  margin-top: 44px;
}
</style>