<template>
  <div class="backstage">
      <div class="lists">
          <div class="list selected" >总览</div>
          <div class="list" @click="gotoList">表单列表</div>
      </div>
      <div class="content">
        <div class="record">
          <span>浏览总人数</span>
          <span class="count">{{userData.allUser}}</span>
        </div>
        <div class="record">
          <span>提交总人数</span>
          <span class="count">{{userData.totalNum}}</span>
        </div>
        <div class="record">
          <span>男生人数</span>
          <span class="count">{{userData.boyNum}}</span>
        </div>
        <div class="record">
          <span>女生人数</span>
          <span class="count">{{userData.girlNum}}</span>
        </div>
        <div class="record">
          <span>男女比例</span>
          <span class="count">{{userData.girlNum/userData.boyNum}}</span>
        </div>
      </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Home",
  data() {
    return {
      userData:{}
    };
  },
  mounted: async function getData() {
    const result = await axios.get('/getData');
    console.log(result.data);
    this.userData = result.data;
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
  padding: 60px;
}
.record {
  font-size: 50px;
  font-weight: bold;
  margin: 30px 0;
}
.count {
  margin-left: 40px;
}
.selected {
  color: blue;
}
</style>
