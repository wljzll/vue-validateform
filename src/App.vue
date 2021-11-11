<template>
  <div class="app2">
    <deForm :model="loginInfo" :rules="rules" ref="loginForm">
      <deFormitem label="用户名" prop="username">
        <deFnput v-model="loginInfo.username"></deFnput>
      </deFormitem>
      <deFormitem label="用户密码" prop="password">
        <deFnput type="password" v-model="loginInfo.password"></deFnput>
      </deFormitem>
      <deFormitem>
        <div type="primary" @click="submitForm('loginForm')"
          >提交</div
        >
      </deFormitem>
    </deForm>
  </div>
</template>
<script>
import deFormitem from "./components/ElFormItem.vue";
import deFnput from "./components/ElInput.vue";
import deForm from "./components/ElForm.vue";

export default {
  components: {
    deForm,
    deFormitem,
    deFnput
  },
  data() {
    return {
      name: "",
      loginInfo: { username: "", password: "" },
      rules: {
        username: [{ required: true, message: "请输入用户名" }],
        password: [{ required: true, message: "请输入密码" }],
      },
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          alert("校验成功");
        } else {
          alert("校验失败");
        }
      });
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
