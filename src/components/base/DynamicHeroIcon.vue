<template>
  <component v-if="isLoaded" :is="heroIcons[name]" />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import * as heroIcons from "@heroicons/vue/24/outline";

export default defineComponent({
  name: "DynamicHeroIcon",
  data() {
    return {
      isLoaded: false,
      heroIcons: heroIcons,
    };
  },
  props: {
    name: String,
  },
  mounted() {
    this.isLoaded = true;
  },
});
</script>
