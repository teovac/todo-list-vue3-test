<template>
  <div class="bg-white shadow p-3 md:p-5 rounded-lg flex items-center">
    <CustomInput
      className="flex-1 mr-4"
      v-model="title"
      placeholder="Type here..."
    />
    <button
      :disabled="!title"
      @click="handleSubmit"
      class="bg-blue-500 disabled:bg-gray-400 flex items-center px-3 py-2 rounded text-white"
    >
      <DynamicHeroIcon class="w-5 stroke-2 mr-2" name="PlusIcon" />
      <span class="hidden md:block">Add Task</span>
      <span class="block md:hidden">Add</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import CustomInput from "./base/CustomInput.vue";
import DynamicHeroIcon from "./base/DynamicHeroIcon.vue";

export default defineComponent({
  components: { CustomInput, DynamicHeroIcon },
  props: {
    msg: String,
  },
  emits: ["submit"],
  setup(_, { emit }) {
    const title = ref("");

    const handleSubmit = () => {
      if (title.value) {
        emit("submit", title.value);
        title.value = "";
      }
    };

    return {
      title,
      handleSubmit,
    };
  },
});
</script>
