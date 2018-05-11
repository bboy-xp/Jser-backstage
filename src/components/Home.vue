<template>
  <div class="backstage">
      <div class="lists">
          <div class="list" >总览</div>
          <div class="list" @click="gotoList">表单列表</div>
      </div>
      <div class="content">
          <div>总人数</div>
      </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {};
  },
  methods: {
      gotoList() {
          this.$router.replace({ path: "/list"});
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
