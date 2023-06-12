<template>
  <div class="inline-flex" :class="className">
    <input
      class="outline-none border-2 rounded border-gray-400 focus:border-gray-600 w-full px-3 py-2"
      type="text"
      v-model="value"
      :placeholder="placeholder"
    />
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from "vue";

export default defineComponent({
  props: {
    modelValue: [Number, String],
    placeholder: String,
    className: String,
  },
  emits: ["update:modelValue"],
  setup(props, { emit }) {
    const value = computed({
      get: () => props.modelValue,
      set: (newVal) => {
        emit("update:modelValue", newVal);
      },
    });

    return {
      value,
    };
  },
});
</script>
