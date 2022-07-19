<template>
  <div class="flex">
    <label v-for="(item, i) in items" :key="i" class="cursor-pointer m-1">
      <div
        class="rounded border border-sky-500 p-1"
        style="width: 200px; height: 200px"
        :style="{ 'background-color': _value === item ? 'red' : 'black' }"
      >
        <input
          v-model="_value"
          name="radio"
          class="radio radio-primary"
          type="radio"
          :value="item"
        />
        <div style="width: 100%; height: 100px">{{ item }}</div>
      </div>
    </label>
  </div>
</template>

<script lang="ts" setup>
type PropsType = {
  items: number[]
  checked: number
}
type EmitType = {
  (e: 'update:checked', value: number): void
}
const props = defineProps<PropsType>()
const emit = defineEmits<EmitType>()

const { checked } = toRefs(props)

const _value = computed({
  get: () => checked.value,
  set: (value) => {
    emit('update:checked', value)
  },
})
</script>
