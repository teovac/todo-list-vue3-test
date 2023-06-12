<template>
  <div class="flex items-center py-2 pl-4 pr-5 rounded-md hover:bg-white">
    <div class="pr-2">
      <CheckBox
        :modelValue="data.completed"
        @update:modelValue="$emit('complete')"
      />
    </div>
    <div class="flex-1 px-3">
      <p
        class="text-md md:text-lg"
        :class="{
          'line-through': data.completed,
        }"
      >
        {{ data.title }}
      </p>
    </div>
    <div>
      <DynamicHeroIcon
        @click="$emit('remove')"
        name="TrashIcon"
        class="w-5 text-red-500 cursor-pointer"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import { ITask } from "@/types/task";
import DynamicHeroIcon from "./base/DynamicHeroIcon.vue";
import CheckBox from "./base/CheckBox.vue";

export default defineComponent({
  components: { CheckBox, DynamicHeroIcon },
  props: {
    data: {
      type: Object as PropType<ITask>,
      required: true,
    },
  },
  emits: ["complete", "remove"],
});
</script>
