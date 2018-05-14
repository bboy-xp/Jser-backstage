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
            width="80">
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
          <el-table-column label="操作" width="150">
            <template slot-scope="scope">
              <el-button
                size="mini"
                @click="handleEdit(scope.$index, scope.row);dialogFormVisible = true">编辑</el-button>
              <el-button
                size="mini"
                type="danger"
                @click="handleDelete(scope.$index, scope.row)">删除</el-button>
            </template>
          </el-table-column>
        </el-table>
        <el-dialog title="收货地址" :visible.sync="dialogFormVisible">
  <el-form :model="form">
    <el-form-item label="openId" :label-width="formLabelWidth">
      <el-input v-model="form.openId" auto-complete="off"></el-input>
    </el-form-item>
    <el-form-item label="姓名" :label-width="formLabelWidth">
      <el-input v-model="form.name" auto-complete="off"></el-input>
    </el-form-item>
    <el-form-item label="性别" :label-width="formLabelWidth">
      <el-input v-model="form.sex" auto-complete="off"></el-input>
    </el-form-item>
    <el-form-item label="年级" :label-width="formLabelWidth">
      <el-input v-model="form.grade" auto-complete="off"></el-input>
    </el-form-item>
    <el-form-item label="专业" :label-width="formLabelWidth">
      <el-input v-model="form.major" auto-complete="off"></el-input>
    </el-form-item>
    <el-form-item label="大学" :label-width="formLabelWidth">
      <el-input v-model="form.college" auto-complete="off"></el-input>
    </el-form-item>
    <el-form-item label="联系方式" :label-width="formLabelWidth">
      <el-input v-model="form.phoneNum" auto-complete="off"></el-input>
    </el-form-item>
    <el-form-item label="等级" :label-width="formLabelWidth">
      <el-input v-model="form.level" auto-complete="off"></el-input>
    </el-form-item>
    <el-form-item label="原因" :label-width="formLabelWidth">
      <el-input v-model="form.reason" auto-complete="off"></el-input>
    </el-form-item>
    <el-form-item label="自我介绍" :label-width="formLabelWidth">
      <el-input v-model="form.introduce" auto-complete="off"></el-input>
    </el-form-item>
    <el-form-item label="其他原因" :label-width="formLabelWidth">
      <el-input v-model="form.otherReason" auto-complete="off"></el-input>
    </el-form-item>
  </el-form>
  <div slot="footer" class="dialog-footer">
    <el-button @click="dialogFormVisible = false">取 消</el-button>
    <el-button type="primary" @click="dialogFormVisible = false">确 定</el-button>
  </div>
</el-dialog>
  
      </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Home",
  data() {
    return {
      userList: [],
      dialogFormVisible: false,
      form: {
        openId: "",
        name: "",
        sex: "",
        grade: "",
        major: "",
        college: "",
        phoneNum: "",
        level: "",
        reason: "",
        introduce: "",
        otherReason: "",
      },
      formLabelWidth: "120px"
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
    },
    handleEdit(index, row) {
      // console.log(index, row);
      // console.log(row.name);
      this.form.openId = row.openId;
      this.form.name = row.name;
      this.form.sex = row.sex;
      this.form.grade = row.grade;
      this.form.major = row.major;
      this.form.college = row.college;
      this.form.phoneNum = row.phoneNum;
      this.form.level = row.level;
      this.form.reason = row.reason;
      this.form.introduce = row.introduce;
      this.form.otherReason = row.otherReason;
    },
    handleDelete(index, row) {
      console.log(index, row);
      this.$confirm('此操作将永久删除该记录, 是否继续?', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning',
          center: true
        }).then(() => {
          this.$message({
            type: 'success',
            message: '删除成功!'
          });
        }).catch(() => {
          this.$message({
            type: 'info',
            message: '已取消删除'
          });
        });
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
