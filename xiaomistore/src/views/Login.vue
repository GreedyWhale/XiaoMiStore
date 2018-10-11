<template>
  <div class="container">
    <h1 class="login-method">{{ loginOptions.method }}</h1>
    <div class="login-input-wrapper">
      <input
        :type="loginOptions.userNameInputType" name="userName"
        :placeholder="loginOptions.userNameInputPlaceholder">
    </div>
    <div class="login-input-wrapper">
      <input
        type="password" name="password"
        :placeholder="loginOptions.passwordInputPlaceholder">
      <button class="get-auth-code-btn">获取验证码</button>
    </div>
    <div class="toggle-login-methoed-btn">
      {{ loginOptions.toggleLoginMethoedBtnDesc }}
      <svg class="right-arrow-icon" aria-hidden="true">
        <use xlink:href="#icon-youjiantou"></use>
      </svg>
    </div>
    <button class="login-button">登录</button>
    <div class="agreement-checkbox-wrapper">
      <input type="checkbox" v-model="checked" class="">
      <p>
        登录即代表同意小米账号
        <router-link to="home">用户协议</router-link>
        和
        <router-link to="home">隐私策略</router-link>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isSMSLogin: true,
      checked: true
    };
  },
  computed: {
    loginOptions() {
      const { isSMSLogin } = this.$data;
      return {
        method: isSMSLogin ? '手机号登录' : '密码登录',
        userNameInputType: isSMSLogin ? 'number' : 'text',
        userNameInputPlaceholder: isSMSLogin
          ? '请输入手机号'
          : '请输入手机号/邮箱/小米账号',
        passwordInputPlaceholder: isSMSLogin
          ? '请输入短信验证码'
          : '请输入密码',
        toggleLoginMethoedBtnDesc: isSMSLogin
          ? '用账号密码登录'
          : '用手机短信登录'
      };
    }
  }
};
</script>

<style lang="scss" scoped>
button {
  outline: none;
  border: none;
}
.container {
  padding: 80px 60px 0;
  .login-method {
    font-weight: 500;
    font-size: 45px;
    margin-bottom: 100px;
  }
  .login-input-wrapper {
    display: flex;
    align-items: center;
    border-bottom: 1px solid #eee;
    padding-bottom: 10px;
    margin-bottom: 70px;
    > input {
      flex: 1;
      border: none;
      outline: none;
      font-size: 32px;
    }
    .get-auth-code-btn {
      padding: 10px 1em;
      font-size: 32px;
      color: #ff7300;
      background: transparent;
    }
  }
  .toggle-login-methoed-btn {
    display: flex;
    align-items: center;
    line-height: 20px;
    font-size: 24px;
    color: #333;
    padding-top: 40px;
    .right-arrow-icon {
      width: 1em;
      height: 1em;
    }
  }
  .login-button {
    display: block;
    width: 100%;
    text-align: center;
    color: #fff;
    font-size: 32px;
    margin-top: 200px;
    background: #ff7300;
    border-radius: 8px;
    padding: 20px 0;
  }
  .agreement-checkbox-wrapper {
    margin-top: 20px;
    color: rgb(151, 151, 151);
    font-size: 24px;
    display: flex;
    align-items: center;
    > input[type='checkbox'] {
      -webkit-appearance: none;
      width: 26px;
      height: 26px;
      background: #fff;
      border: #999 solid 1px;
      border-radius: 3px;
      display: flex;
      align-items: center;
      justify-content: center;
      outline: none;
      &:checked {
        background: #ff7300;
        border-color: transparent;
      }
      &:checked::after {
        content: '';
        background: transparent;
        border: #fff solid 2px;
        border-top: none;
        border-right: none;
        height: 6px;
        width: 10px;
        transform: rotate(-45deg);
      }
    }
    a {
      color: inherit;
    }
  }
}
</style>
