<template>
  <div class="backstage">
      <div class="lists">
          <div class="list" @click="gotoHome">总览</div>
          <div class="list">表单列表</div>
      </div>
      <div class="content">
      </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Home",
  data() {
    return {};
  },
  mounted: async function getList() {
      const result = await axios.get('/getList');
      console.log(result);
  }
  ,
  methods: {
      gotoHome() {
          this.$router.replace({ path: "/"});
      }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.backstage {
  display: flex;
  height: 100vh;
  width: 100vw;
  overflow: hidden;
  /* border: 1px solid #000000; */
  /* flex-direction: column */
}
.lists {
  display: flex;
  flex-direction: column;
  flex-basis: 15%;
  padding-top: 50px;
  /* border-right: 1px solid #000000; */
}
.list {
  margin: 20px auto 20px auto;
}
.content {
  flex: 1;
  padding: 30px;
}
</style>
