<template>
  <div id="basicLayout">
    <!-- 最小高度， vh屏幕可视区域-->
    <a-layout style="min-height: 100vh">
      <a-layout-header class="header">
        <GlobalHeader />
      </a-layout-header>
      <a-layout-content class="content">
        <router-view />
      </a-layout-content>
      <a-layout-footer class="footer">
        <a
          href="https://mp.csdn.net/mp_blog/manage/article?spm=3001.5298"
          target="_blank"
          >站长博客</a
        >
      </a-layout-footer>
    </a-layout>
  </div>
</template>

<script setup lang="ts">
import GlobalHeader from "@/components/GlobalHeader.vue";
</script>

<style scoped>
#basicLayout {
}

#basicLayout .header {
  margin-bottom: 16px;
  box-shadow: #eee 1px 1px 5px;
  //background: #42b983;
}

#basicLayout .content {
  background: linear-gradient(to right, #fefefe, #fff);
  margin-bottom: 16px;
}

#basicLayout .footer {
  background: #efefef;
  padding: 16px;
  position: sticky;
  bottom: 0;
  left: 0;
  right: 0;
  text-align: center;
}
</style>
