<template>
  <div class="grid grid-cols-2 divide-x">
    <div class="Mitte">
      <h3>QrCode:</h3>
      <input style="margin: 10px" v-model="value" type="text" />
      <button class="bg-sky-500 hover:bg-sky-700 ..." @click="forceRerender()">
        save changes
      </button>
      <qrcode-vue
        v-if="renderComponent"
        :value="value"
        :size="size"
        level="L"
      />
    </div>
    <div class="Mitte">
      <h3>QrCode:</h3>
      <input style="margin: 10px" v-model="value" type="text" />
      <button class="bg-sky-500 hover:bg-sky-700 ..." @click="forceRerender()">
        save changes
      </button>
      <qrcode-vue
        v-if="renderComponent"
        :value="value"
        :size="size"
        level="L"
      />
    </div>
  </div>
</template>

  <script setup>
import QrcodeVue from "qrcode.vue";
import { nextTick, ref } from "vue";

const value = reactive("https://www.linkplotter.com/");
const size = reactive(400);

const renderComponent = ref(true);

const forceRerender = async () => {
  // Remove MyComponent from the DOM
  renderComponent.value = false;

  // Wait for the change to get flushed to the DOM
  await nextTick();

  // Add the component back in
  renderComponent.value = true;
};
</script>

  <style>
.Mitte {
  display: flex;
  flex-direction: column;
  padding: 10px;
}
.button {
  padding: 8px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  margin-left: 6px;
  font-size: 14px;
  cursor: pointer;
}
</style>