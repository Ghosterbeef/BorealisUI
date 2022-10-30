<template>
  <Popper v-bind="popperConfig" :show="isOpened" :disabled="disabled">
    <BorealisSelectBody v-model:search-value="searchValue" v-bind="selectBodyProps"/>
    <template #content>
      <BorealisSelectDropdown/>
    </template>
  </Popper>
</template>

<script>
export default {
  name: "BorealisSelect"
}
</script>

<script setup>
import Popper from 'vue3-popper'
import BorealisSelectBody from "@/components/BorealisSelect/BorealisSelectBody.vue";
import BorealisSelectDropdown from "@/components/BorealisSelect/BorealisSelectDropdown.vue";
import {computed, ref} from "vue";

const props = defineProps({
  modelValue: {
    type: [Array, String],
    required: true
  },
  placeholder: String,
  disabled: Boolean
})

const popperConfig = Object.freeze({
  placement: 'bottom-start',
  offsetDistance: '-1'
})

const isOpened = ref(false)
const searchValue = ref('')


const selectBodyProps = computed(() => ({
  value: props.modelValue,
  disabled: props.disabled,
  placeholder: props.placeholder
}))

</script>

<style scoped lang="scss">

</style>
