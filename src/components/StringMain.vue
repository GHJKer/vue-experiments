<script lang="ts" setup>
import { ref } from "vue";

interface Props {
  text?: string;
}

defineProps<Props>();

let cubeRef = ref();

let rotateY = ref(0);
let rotateX = ref(0);

document.onkeydown = function (e) {
  if (e.key === "ArrowLeft") rotateY.value -= 4;
  if (e.key === "ArrowRight") rotateY.value += 4;
  if (e.key === "ArrowUp") rotateX.value -= 4;
  if (e.key === "ArrowDown") rotateX.value += 4;

  cubeRef.value.style.transform = `rotateY(${rotateY.value}deg) rotateX(${rotateX.value}deg)`;
};

function changeAngle() {
  cubeRef.value.style.transform = "rotateY(16deg) rotateX(-22deg)";
}

function returnAngle() {
  cubeRef.value.style.transform = "rotateY(16deg) rotateX(-12deg)";
  cubeRef.value.style = "";
}
</script>
<template>
  <div :class="$style['container']">
    <div
      ref="cubeRef"
      :class="$style['cube']"
      @mousedown="changeAngle"
      @mouseup="returnAngle"
      @mouseout="returnAngle"
    >
      <div :class="[$style['side'], $style['front']]">{{ text }}</div>
      <div :class="[$style['side'], $style['back']]">back</div>
      <div :class="[$style['side'], $style['right']]">right</div>
      <div :class="[$style['side'], $style['left']]">left</div>
      <div :class="[$style['side'], $style['top']]">top</div>
      <div :class="[$style['side'], $style['bottom']]">bottom</div>
    </div>
  </div>
</template>

<style module>
.container {
  position: relative;
  /* margin: 200px auto; */
  width: 215px;
  height: 50px;
  perspective: 500px;
}

.cube {
  width: inherit;
  height: inherit;
  transform-style: preserve-3d;
  transition: transform 0.2s ease 0s;
}

.cube:hover {
  transform: rotateY(16deg) rotateX(-12deg);
}

.side {
  position: absolute;
  width: inherit;
  height: inherit;
  border: 1px solid #fff;
  font: normal 20px Arial;
  text-align: center;
  /* backface-visibility: hidden; */
  background-color: #7b7575;
}

.front {
  transform: translateZ(25px);
  width: 215px;
  height: 25px;
}

.back {
  transform: rotateY(180deg) translateZ(25px);
  width: 215px;
  height: 25px;
}

.right {
  transform: rotateY(90deg) translateZ(190px);
  height: 25px;
  width: 50px;
}

.left {
  transform: rotateY(-90deg) translateZ(25px);
  height: 25px;
  width: 50px;
}

.top {
  transform: rotateX(90deg) translateZ(25px);
  width: 215px;
}

.bottom {
  transform: rotateX(-90deg) translateZ(0px);
  width: 215px;
}
</style>
