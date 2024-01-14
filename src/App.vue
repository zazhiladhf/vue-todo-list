<script>
import ItemComponent from "./components/ItemComponent.vue";
import TodoList from "./components/TodoList.vue";

export default {
  components: {
    ItemComponent,
    TodoList,
  },
  data() {
    return {
      items: [
        {
          id: 1,
          text: "item 1",
        },
        {
          id: 2,
          text: "item 2",
        },
      ],
    };
  },
};
</script>

<template>
  <!-- <h1>Hello</h1> -->
  <TodoList />
</template>

<style scoped>
body {
  color: black;
}
</style>
