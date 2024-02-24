<script setup lang="ts">
import QRConvert from './components/QRConvert.vue'
</script>

<template>
  <div class="titlebar">
    <h3 class="title">PeiFang's Tools</h3>
  </div>
  <div class="mainbody">
    <ElMenu class="menu">
      <ElMenuItem index="0">二维码转换</ElMenuItem>
      <ElMenuItem index="1">未完待续</ElMenuItem>
    </ElMenu>
    <div class="main">
      <QRConvert></QRConvert>
    </div>
  </div>
</template>

<style scoped>
.titlebar {
  height: 6vh;
  position: sticky;
  top: 0%;
  display: flex;
  align-items: center;
  background-color: rgba(73, 177, 245, 0.85);
}

.title {
  margin: 10px;
  margin-left: 30px;
}

.mainbody {
  height: 94vh;
  display: flex;
  flex-direction: row;
}

.main {
  flex: 1;
}

.menu {
  height: 100%;
}
</style>
