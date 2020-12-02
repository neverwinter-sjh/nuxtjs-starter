<template>
  <ul>
    <li v-for="todo in todos" :key="todo.text">
      <input :checked="todo.done" type="checkbox" @change="toggle(todo)" />
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
    </li>
    <li><input placeholder="What needs to be done?" @keyup.enter="addTodo" /></li>
  </ul>
</template>

<script>
import { mapMutations } from 'vuex';

export default {
  computed: {
    todos() {
      return this.$store.state.store.list;
    }
  },
  methods: {
    addTodo(e) {
      this.$store.commit('store/add', e.target.value);
      e.target.value = '';
    },
    ...mapMutations({
      toggle: 'store/toggle'
    })
  }
};
</script>

<style>
.done {
  text-decoration: line-through;
}
</style>
