<template>
  <li class="w-full relative">
    <label class="text-base md:text-lg block mb-2">{{ labelText }}</label>
    <Field
      :name="name"
      :type="type"
      :rules="rules"
      :validate-on-input="true"
      class="border border-black rounded-md bg-transparent focus:border focus:border-black focus:outline-none px-4 py-3 text-lg w-full block text-black mb-10"
      :placeholder="placeholder"
    />
    <ErrorMessage :name="name" class="text-red-600 absolute -bottom-8" />
  </li>
</template>

<script setup>
import { ErrorMessage, Field } from "vee-validate";
import { computed } from "vue";

const props = defineProps({
  name: String,
  type: String,
  rules: String,
  placeholder: String,
});

const labelText = computed(() =>
  props.name
    .split("_")
    .map((el) =>
      el.length !== 0 ? el[0].toLocaleUpperCase() + el.slice(1, el.length) : el
    )
    .join(" ")
);
</script>
