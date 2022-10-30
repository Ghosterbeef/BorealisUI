<template>
  <div class="borealis_select_body_value_placeholder">
    {{ placeholder ? placeholder : '&nbsp;'}}
  </div>
</template>

<script>
export default {
  name: "BorealisSelectBodyValuePlaceholder"
}
</script>

<script setup>
const props = defineProps({
  placeholder: String
})
</script>

<style scoped>

</style>
