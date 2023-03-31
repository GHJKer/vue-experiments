<script setup lang="ts">
import HeaderMain from "./HeaderMain.vue";
import StringMain from "./StringMain.vue";

let myWorks = ["1", "2", "3", "4"];
</script>

<template>
  <div>
    <HeaderMain />
    <div :class="$style['main-container']">
      <div :class="$style['my-work']" v-for="item in myWorks">{{ item }}</div>
    </div>
  </div>
</template>

<style module>
.main-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 30px;
}

.my-work {
  width: 900px;
  height: 700px;
  border: 1px solid #fff;
}
</style>
