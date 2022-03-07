<script setup lang="ts">
import { onMounted } from "vue";

let flys: NodeListOf<HTMLImageElement>;

const mousemove = (evt: any) => {
  flys.forEach(it => {
    let x = it.getBoundingClientRect().left + it.clientWidth / 2;
    let y = it.getBoundingClientRect().top + it.clientHeight / 2;
    let radian = Math.atan2(evt.x - x, evt.y - y);
    let rot = radian * (180 / Math.PI) * -1;
    let rotate = `rotate(${rot}deg)`;
    it.style.transform = rotate;
  });
};

const init = () => {
  flys = document.querySelectorAll("img");
  window.addEventListener("mousemove", mousemove, false);
};

onMounted(init);
</script>

<template>
  <div id="index">
    <img src="@/assets/images/fly1.png" />
    <img src="@/assets/images/fly2.png" />
  </div>
</template>

<style lang="scss" scoped>
#index {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: space-around;

  img {
    width: 300px;
  }
}
</style>
