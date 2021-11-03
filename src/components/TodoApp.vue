<template>
  <div>
    <div class="item">
      <p>Nowe todo: {{ newItem }}</p>
      <input type="text" placeholder="add" v-model="newItem" />
      <button @click="add">Add</button>
    </div>

    <TodoItem @removeItemById="removeItem" @toggleClick="toggleVisibility" v-bind:item="item" v-for="item in items" v-bind:key="item.id" />
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  components: {
    TodoItem,
  },
  data() {
    return {
      newItem: "",
      items: [
        { id: 1042, title: "task", completed: false },
        { id: 1011, title: "eat", completed: true },
      ],
    };
  },
  methods: {
    add() {
      this.items.push({
        id: Math.floor(Math.random() * 1234),
        title: this.newItem,
        completed: false,
      });
      this.newItem = "";
      console.log(this.items);
    },
    toggleVisibility(id) {
      const index = this.items.findIndex((el) => el.id === id);
      this.items[index].completed = !this.items[index].completed;
    },
    removeItem(id){
      const index = this.items.findIndex((el) => el.id === id);
      this.items.splice(index, 1);
    }
  },
};
</script>

<style>
.item {
  border: 1px solid #cdcdcd;
  margin: 8px;
  padding: 10px;
}
.completed {
  opacity: 0.5;
}
.completed h2 {
  text-decoration: line-through;
}
</style>