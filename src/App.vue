<template>
  <div class="showcase">
    <BorealisSelect v-model="value" placeholder="Выберите значение"/>
    <BorealisSelect v-model="value1" />
  </div>
</template>

<script setup>
import BorealisSelect from "@/components/BorealisSelect/BorealisSelect.vue";
import {ref} from "vue";

const value = ref("")
const value1 = ref([])
</script>

<style>
*, *::before, *::after {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html, body, #app {
    height: 100%
}

.showcase {
    display: grid;
    height: 100%;
    gap: 20px;
    place-items: center;
}
</style>
