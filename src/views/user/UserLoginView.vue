<template>
  <div id="userLoginView">
    <h2 style="margin-bottom: 36px">用户登录</h2>
    <a-form
      :model="form"
      @submit="handleSubmit"
      style="max-width: 440px; margin: 0 auto"
      label-align="left"
      auto-label-width
    >
      <a-form-item field="userAccount" label="账号">
        <a-input v-model="form.userAccount" placeholder="请输入账号" />
      </a-form-item>
      <a-form-item field="userPassword" tooltip="密码不少于 8 位" label="密码">
        <a-input-password
          v-model="form.userPassword"
          placeholder="请输入密码"
        />
      </a-form-item>
      <a-form-item>
        <a-button type="primary" html-type="primary" style="width: 120px"
          >登录</a-button
        >
      </a-form-item>
    </a-form>
  </div>
</template>

<script setup lang="ts">
import { reactive } from "vue";
import { UserControllerService, UserLoginRequest } from "../../../generated";
import message from "@arco-design/web-vue/es/message";
import { useRouter } from "vue-router";
import { useStore } from "vuex";

const router = useRouter();
const store = useStore();

/**
 * 表单信息
 */
const form = reactive({
  userAccount: "",
  userPassword: "",
} as UserLoginRequest);

/**
 * 提交表单，执行登录
 */
const handleSubmit = async () => {
  const res = await UserControllerService.userLoginUsingPost(form);
  // 登录成功则跳转到主页
  if (res.code === 0) {
    await store.dispatch("user/getLoginUser");
    await router.push({
      path: "/",
      replace: true,
    });
  } else {
    message.error("登录失败，原因：" + res.message);
  }
};
</script>
