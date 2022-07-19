<template>
  <div>
    <Radio v-model:checked="_value" :items="items" />
    <p>{{ _value }}</p>
  </div>
</template>

<script lang="ts" setup>
const value = ref(0)
const items = ref([1, 2, 3, 4, 5])
const _value = computed({
  get: () => value.value,
  set: (val) => (value.value = val),
})
</script>
