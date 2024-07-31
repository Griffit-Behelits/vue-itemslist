<template>
  <select v-model:="props.modelValue" @change="changeOption">
    <option disabled value="">Выбрать из списка</option>
    <option v-for="option in options" :value="option.value" :key="option.value">
      {{ option.name }}
    </option>
  </select>
</template>

<script setup>
const props = defineProps({
  modelValue: String,
  options: Array,
});

const emit = defineEmits(["update:modelValue"]);

const changeOption = (event) => {
  emit("update:modelValue", event.target.value);
};
</script>

<style></style>
