<template>
  <div class="borealis_select_body">
    <BorealisSelectBodySearch v-model:search-value="searchInput"/>
    <BorealisSelectBodyValuePlaceholder v-if="isEmpty" :placeholder="placeholder"/>
    <BorealisSelectBodyValueSingle v-else-if="!isMulti"/>
    <BorealisSelectValueMultiple v-else/>
  </div>
</template>

<script>
export default {
  name: "BorealisSelectBody"
}
</script>

<script setup>
import BorealisSelectBodySearch from "@/components/BorealisSelect/BorealisSelectBodySearch.vue";
import {computed} from "vue";
import BorealisSelectBodyValuePlaceholder from "@/components/BorealisSelect/BorealisSelectBodyValuePlaceholder.vue";
import BorealisSelectBodyValueSingle from "@/components/BorealisSelect/BorealisSelectBodyValueSingle.vue";
import BorealisSelectValueMultiple from "@/components/BorealisSelect/BorealisSelectBodyValueMultiple.vue";

const emits = defineEmits(['update:search-value'])

const props = defineProps({
  value: {
    type: [Array, String],
    required: true
  },
  searchValue: String,
  placeholder: String
})

const searchInput = computed({
  get() {
    return props.searchValue
  },
  set(val) {
    emits('update:search-value', val)
  }
})
const isMulti = computed(() => Array.isArray(props.value))
const isEmpty = computed(() => isMulti.value ? !props.value.length : !props.value)

</script>

<style scoped lang="scss">
.borealis_select_body {
  min-width: 200px;
  position: relative;
  padding: 8px 16px;
  background-color: #fff;
  border-radius: 4px;
  border: 1px solid #333;
}
</style>
