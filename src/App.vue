<template>
  <div class="w-screen h-screen bg-gray-200 overflow-auto p-3 md:p-5">
    <div class="max-w-container m-auto">
      <h1 class="text-4xl font-bold underline text-center text-blue-400 mb-6">
        My Tasks
      </h1>

      <TaskForm @submit="createTask" />
      <div class="border border-gray-300 my-3 md:my-5" />
      <div>
        <TaskItem
          v-for="(task, index) in tasks"
          :key="`task-${index}`"
          :data="task"
          @complete="completeTask(index)"
          @remove="removeTask(index)"
        />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { ITask } from "@/types/task";
import TaskForm from "@/components/TaskForm.vue";
import TaskItem from "@/components/TaskItem.vue";

const tasks = ref<ITask[]>([
  {
    title: "Buy groceries for next week",
    completed: false,
  },
  {
    title: "Renew car insurance",
    completed: false,
  },
  {
    title: "Sign up for online course",
    completed: true,
  },
  {
    title: "Pay electricity bill",
    completed: false,
  },
]);

const createTask = (title: string) => {
  tasks.value = [...tasks.value, { title, completed: false }];
};

const completeTask = (i: number) => {
  tasks.value = tasks.value.map((task, index) => ({
    ...task,
    completed: i === index ? true : task.completed,
  }));
};

const removeTask = (i: number) => {
  tasks.value = tasks.value.filter((_, index) => i !== index);
};
</script>
