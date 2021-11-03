<template>
  <div
    class="item"
    v-bind:class="{
      completed: item.completed == true,
    }"
  >
    <h2>{{ item.title }}</h2>
    <button v-if="!item.completed" @click="toggleClick">Done</button>
    <button v-else @click="toggleClick">not done</button>
    <button @click="removeItemById">X</button>
  </div>
</template>

<script>
export default {
  props: ["item"],
  methods: {
    toggleClick() {
      this.$emit("toggleClick", this.item.id);
    },
    removeItemById() {
      this.$emit("removeItemById", this.item.id);
    },
  },
};
</script>