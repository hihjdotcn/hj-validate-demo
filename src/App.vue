<!--
 * @Description: entry page
 * @LastEditors: hj
 * @LastEditTime: 2022-05-16 09:43:58
-->
<template>
  <div id="app">
    <el-form :model="form" :rules="rules" ref="form" label-width="100px" class="form-container">
      <el-form-item label="手机号码" prop="phone">
        <el-input v-model="form.phone"></el-input>
      </el-form-item>
      <el-form-item label="电话号码" prop="telephone">
        <el-input v-model="form.telephone"></el-input>
      </el-form-item>
      <el-form-item label="用户名" prop="userName">
        <el-input v-model="form.userName"></el-input>
      </el-form-item>
      <el-form-item label="密码" prop="password">
        <el-input v-model="form.password"></el-input>
      </el-form-item>
      <el-form-item label="中文名" prop="chineseName">
        <el-input v-model="form.chineseName"></el-input>
      </el-form-item>
      <el-form-item label="电子邮箱" prop="email">
        <el-input v-model="form.email"></el-input>
      </el-form-item>
      <el-form-item label="身份证" prop="idCard">
        <el-input v-model="form.idCard" maxlength="18"></el-input>
      </el-form-item>
      <el-form-item label="邮政编码" prop="postCard">
        <el-input v-model="form.postCard"></el-input>
      </el-form-item>
      <el-form-item label="uri地址" prop="uri">
        <el-input v-model="form.uri"></el-input>
      </el-form-item>
      
      <el-form-item>
        <el-button type="primary" @click="submitForm('form')">提交</el-button>
        <el-button @click="resetForm('form')">清空</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
import { vPhone,vTelephone,vUserName,vPassword,vChinese,vEmail,vIdCard, vPostCard,vURI} from './utils/index'

export default {
  name: 'App',
  data() {
    var rPhone = (rule, value, callback) => {
      let warnPhone = vPhone(value)
      if (warnPhone) {
        callback(new Error(warnPhone));
      } else {
        callback();
      }
    }
    var rTelephone = (rule, value, callback) => {
      let warnTel = vTelephone(value)
      if (warnTel) {
        callback(new Error(warnTel));
      } else {
        callback();
      }
    }
    var rUserName = (rule, value, callback) => {
      let warnMsg = vUserName(value)
      if (warnMsg) {
        callback(new Error(warnMsg));
      } else {
        callback();
      }
    }
    var rPassword = (rule, value, callback) => {
      let warnMsg = vPassword(value)
      if (warnMsg) {
        callback(new Error(warnMsg));
      } else {
        callback();
      }
    }
    var rChinese = (rule, value, callback) => {
      let warnMsg = vChinese(value)
      if (warnMsg) {
        callback(new Error(warnMsg));
      } else {
        callback();
      }
    }
    var rEmail = (rule, value, callback) => {
      let warnMsg = vEmail(value)
      if (warnMsg) {
        callback(new Error(warnMsg));
      } else {
        callback();
      }
    }
    var rIdCard = (rule, value, callback) => {
      let warnMsg = vIdCard(value)
      if (warnMsg) {
        callback(new Error(warnMsg));
      } else {
        callback();
      }
    }
    var rPostCard = (rule, value, callback) => {
      let warnMsg = vPostCard(value)
      if (warnMsg) {
        callback(new Error(warnMsg));
      } else {
        callback();
      }
    }
    var rURI = (rule, value, callback) => {
      let warnMsg = vURI(value)
      if (warnMsg) {
        callback(new Error(warnMsg));
      } else {
        callback();
      }
    }

    return {
      form: {
        phone: '',
        telephone: '',
        userName: '',
        chineseName: '',
        password: '',
        email: '',
        idCard: '',
        postCard: '',
        uri: '',
      },
      rules: {
        phone: [
          { required: true, message: '请输入手机号码', trigger: ['blur','change'] },
          { validator: rPhone, trigger: ['blur','change']}
        ],
        telephone: [
          { validator: rTelephone, trigger: ['blur','change']}
        ],
        userName: [
          { validator: rUserName, trigger: ['blur','change']}
        ],
        chineseName: [
          { validator: rChinese, trigger: ['blur','change']}
        ],
        password: [
          { validator: rPassword, trigger: ['blur','change']}
        ],
        email: [
          { validator: rEmail, trigger: ['blur','change']}
        ],
        idCard: [
          { validator: rIdCard, trigger: ['blur','change']}
        ],
        postCard: [
          { validator: rPostCard, trigger: ['blur','change']}
        ],
        uri: [
          { validator: rURI, trigger: ['blur','change']}
        ],
      }
    }
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          alert('submit!');
        } else {
          console.log('error submit!!');
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.form-container{
  width:400px;
}
</style>
