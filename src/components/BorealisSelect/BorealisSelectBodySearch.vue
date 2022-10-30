<template>
  <input
    class="borealis_select_body_search"
    type="text"
    v-model="searchInput"
    @focus="onSearchFocus"
  >
</template>

<script>
export default {
  name: "BorealisSelectBodySearch"
}
</script>

<script setup>
import {computed, ref} from "vue";

const emits = defineEmits(['focus', 'update:search-value'])

const props = defineProps({
  searchValue: String,
})

const searchTimeout = ref(null)

const searchInput = computed({
  get() {
    return props.searchValue
  },
  set(val) {
    if (searchTimeout.value) clearTimeout(searchTimeout.value)
    searchTimeout.value = setTimeout(() => {
      emits('update:search-value', val)
      searchTimeout.value = null
    }, 500)
  }
})

const onSearchFocus = () => {
  emits('focus')
}
</script>

<style scoped lang="scss">
.borealis_select_body_search {
  position: absolute;
  inset: 0;
  border: none;
  outline: none;
  border-radius: 4px;
  padding: 8px 16px;
}
</style>
