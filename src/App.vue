<template>
  <header>
    <button
      v-for="device in devices"
      :key="device.mode"
      :class="{ hidden: !device.show }"
      @click="onToggleShow(device)"
    >
      {{ device.name }}
    </button>
  </header>
  <div class="devices">
    <DeviceFrame
      v-for="device in shownDevices"
      :key="device.name"
      :name="device.name"
      :mode="device.mode"
      :skin="device.skin"
    />
  </div>
</template>

<script setup>
import { computed, ref } from "vue";
import DeviceFrame from "@/components/DeviceFrame.vue";
import androidSkin from "./assets/android-device-skin.png";
import iphoneSkin from "./assets/iphone-device-skin.png";

const devices = ref([
  { name: "Android", mode: "md", skin: androidSkin, show: true },
  { name: "iOS", mode: "ios", skin: iphoneSkin, show: true },
]);

const shownDevices = computed(() => devices.value.filter((d) => d.show));

const onToggleShow = (device) => {
  device.show = !device.show;
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

*,
*:before,
*:after {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

html {
  background-color: #242a31;
}

body {
  margin: 0;
}
</style>

<style scoped>
header {
  height: 5rem;
  background-color: #151a21;
  display: flex;
  justify-content: center;
}

button {
  margin: 1rem;
  cursor: pointer;
  min-width: 4rem;
  height: 3rem;
  min-width: 6rem;
  background-color: white;
  box-shadow: none;
  border: none;
  box-shadow: 1px 1px 2px grey;
}

button.hidden {
  opacity: 0.75;
}

.devices {
  display: flex;
  justify-content: space-around;
  align-items: center;
  min-height: calc(100vh - 5rem);
}
</style>
