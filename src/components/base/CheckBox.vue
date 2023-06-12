<template>
  <div
    class="w-5 h-5 rounded border-2 flex items-center justify-center cursor-pointer"
    :class="{
      'bg-white border-gray-500': !modelValue,
      'bg-blue-600 border-blue-600': modelValue,
    }"
    @click="$emit('update:modelValue', !modelValue)"
  >
    <DynamicHeroIcon v name="CheckIcon" class="w-4 text-white stroke-2" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import DynamicHeroIcon from "./DynamicHeroIcon.vue";

export default defineComponent({
  components: { DynamicHeroIcon },
  props: {
    modelValue: Boolean,
  },
  emits: ["update:modelValue"],
});
</script>
