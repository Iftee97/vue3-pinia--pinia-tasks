<template>
  <div class="task">
    <h3>{{ task.title }}</h3>
    <div class="icons">
      <i class="material-icons" @click="handleDelete(task.id)">delete</i>
      <i
        class="material-icons"
        :class="{ active: task.isFav }"
        @click="toggleFav(task.id)"
      >
        favorite
      </i>
    </div>
  </div>
</template>

<script>
import { useTaskStore } from "../stores/TaskStore";

export default {
  name: "TaskDetails",

  props: ["task"],

  setup() {
    const taskStore = useTaskStore();

    const handleDelete = (id) => {
      taskStore.deleteTask(id);
    };

    const toggleFav = (id) => {
      taskStore.toggleFav(id);
    };

    return {
      handleDelete,
      toggleFav,
    };
  },
};
</script>