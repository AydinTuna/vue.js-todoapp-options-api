<template>
  <div class="content">
    <h1>Intro to vue 3</h1>
    <form @submit.prevent="newTodo">
      <div class="field">
        <label class="label">Label</label>
        <div class="control">
          <input class="input" type="text" placeholder="Ödev yap" ref="input" />
        </div>
      </div>
      <button class="button is-warning">Ekle</button>
    </form>

    <div v-for="todo in todos" :key="todo.id" class="card my-5 mx-5">
      <div class="card-content">
        <div class="media">
          <div class="media-left"></div>
          <div class="media-content">
            <p
              :class="{ done: todo.done }"
              @click="toggleDone(todo)"
              class="title is-4 cursor"
            >
              {{ todo.content }}
            </p>
            <p class="subtitle is-6">Done: {{ todo.done }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      done: false,
      todos: [],
    };
  },
  mounted() {
    this.$refs.input.focus();
  },
  methods: {
    newTodo() {
      this.todos.push({
        content: this.$refs.input.value,
        done: this.done,
        id: Date.now(),
      });
      this.$refs.input.value = "";
      this.$refs.input.focus();
    },
    toggleDone(todo) {
      todo.done = !todo.done;
    },
  },
};
</script>

<style lang="scss">
.cursor {
  cursor: pointer;
}

.done {
  text-decoration: line-through;
}
</style>
