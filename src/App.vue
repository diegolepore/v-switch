<template>
  <button @click="changeNumber">Change</button>
  <button @click="number = 10">Change to 10</button>
  {{ number }}
  <!-- <button @click="size = 'big'">Big</button>
  <button @click="size = 'small'">Small</button>
  <button @click="size = 'invalid'">Invalid</button> -->

  <v-switch :case="number">
    <template v-for="num in numbers" v-slot:[num]> Number: {{ num }} </template>

    <template #default> Default </template>
  </v-switch>

  <!-- <v-switch :case="size">
    <template #big> Big </template>

    <template #small> Small </template>

    <template #default> Default </template>
  </v-switch> -->
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import { VSwitch } from "./components/v-switch";
export default defineComponent({
  components: {
    VSwitch,
  },
  setup() {
    const number = ref(1);
    const numbers = [1, 2, 3, 4, 5];
    const changeNumber = () => {
      const rand = Math.ceil(Math.random() * 5);
      number.value = rand;
    };
    type Size = "small" | "big" | "invalid";
    const size = ref<Size>("small");

    return {
      changeNumber,
      number,
      numbers,
      size,
    };
  },
});
</script>