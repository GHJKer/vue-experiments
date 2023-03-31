<script lang="ts" setup>
import StringMain from "./StringMain.vue";

const mainMenu = ["Контакты", "Обо мне", "Мой технический стек", "Мои проекты"];
</script>

<template>
  <div :class="$style['main-container']">
    <ul :class="$style['header-list']">
      <li v-for="item in mainMenu"><StringMain :text="item" /></li>
    </ul>
  </div>
</template>

<style module>
.main-container {
  display: flex;
  justify-content: center;
}

.header-list {
  display: flex;
  gap: 50px;
}
</style>
