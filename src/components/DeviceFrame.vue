<template>
  <div ref="deviceFrame" class="device-frame">
    <div class="name" @click="onRefresh()">{{ name }}</div>
    <div class="skin">
      <iframe ref="iframe" :src="`http://localhost:8100?mode=${mode}`" />
      <div
        class="skin-wrapper"
        :style="{ 'background-image': `url(${skin})` }"
      ></div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

defineProps({
  name: String,
  skin: String,
  mode: {
    type: String,
    required: true,
    validator: (v) => ["md", "ios"].includes(v),
  },
});

const iframe = ref();

const onRefresh = () => {
  iframe.value.src += "";
};
</script>

<style scoped>
.device-frame {
  width: 350px;
}

.name {
  color: rgb(230, 230, 230);
  font-size: 1.5rem;
}

.skin {
  height: 730px;
  width: 100%;
  position: relative;
}

.skin-wrapper {
  pointer-events: none;
  height: 100%;
  width: 100%;
  background-size: 100% 100%;
  position: relative;
  top: -100%;
}

iframe {
  padding-top: 10px;
  padding-bottom: 8px;
  width: 100%;
  height: 100%;
  border: none;
}
</style>
