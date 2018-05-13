<template>
  <div class="backstage">
      <div class="lists">
          <div class="list" @click="gotoHome">总览</div>
          <div class="list selected">表单列表</div>
      </div>
      <div class="content">
        <el-table
    :data="userList"
    border
    style="width: 100%">
    <el-table-column
      prop="date"
      label="日期"
      >
    </el-table-column>
    <el-table-column
      prop="openId"
      label="openId"
      >
    </el-table-column>
    <el-table-column
      prop="name"
      label="姓名"
      >
    </el-table-column>
    <el-table-column
      prop="sex"
      label="性别"
      width="50">
    </el-table-column>
    <el-table-column
      prop="grade"
      label="年级">
    </el-table-column>
    <el-table-column
      prop="major"
      label="专业">
    </el-table-column>
    <el-table-column
      prop="college"
      label="大学">
    </el-table-column>
    <el-table-column
      prop="phoneNum"
      label="联系电话">
    </el-table-column>
    <el-table-column
      prop="level"
      label="等级">
    </el-table-column>
    <el-table-column
      prop="reason"
      label="原因"
      width="75">
    </el-table-column>
    <el-table-column
      prop="otherReason"
      label="其他原因">
    </el-table-column>
    <el-table-column
      prop="introduce"
      label="自我介绍">
    </el-table-column>
  </el-table>
      </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Home",
  data() {
    return {
      userList: []
    };
  },
  mounted: async function getList() {
    let result = await axios.get("/getList");
    // console.log(result.data);
    this.userList = result.data;
  },
  methods: {
    gotoHome() {
      this.$router.replace({ path: "/" });
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
.selected {
  color: blue;
}
.content {
  flex: 1;
  padding: 30px;
  display: flex;
}
</style>
