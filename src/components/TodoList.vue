<template>
  <div>
    <link
      href="https://fonts.googleapis.com/css?family=Reenie+Beanie"
      rel="stylesheet"
    />
    <link
      href="https://fonts.googleapis.com/css?family=Cutive+Mono"
      rel="stylesheet"
    />
    <add-todo @add-todo="addList" />
    <div style="display: flex; gap: 1em; justify-content: center">
      <div class="lined-paper">
        <div class="top-margin"></div>
        <div class="left-margin">
          <p>Yapılacaklar</p>
          <ul>
            <li v-for="(todo, index) in todos" :key="index">
              <div v-if="!todo.check" class="card">
                <div class="checkButton">
                  <input type="checkbox" v-model="todo.check" />
                </div>
                <div class="todosList">
                  {{ todo.title }}
                </div>
              </div>
            </li>
          </ul>
        </div>
      </div>
      <done :todos="todos" />
    </div>
  </div>
</template>
<script>
import AddTodo from "./AddTodo.vue";
import Done from "./Done.vue";
export default {
  components: { AddTodo, Done },
  data() {
    return {
      todos: [
        {
          title: "Alışverişe Çık",
          check: false,
        },
        {
          title: "Vue çalış",
          check: true,
        },
        {
          title: "Yemek Yap",
          check: false,
        },
        {
          title: "İş Bul",
          check: false,
        },
      ],
      addTodo: "",
    };
  },
  methods: {
    addList(e) {
      this.todos.push({
        title: e,
        check: false,
      });
    },
  },
};
</script>
<style scoped>
.lined-paper {
  position: relative;
  width: 38%;
  height: 426px;
  top: 1em;
  background: linear-gradient(to bottom, #f2f2ef 0%, #f2f2ef 97%, #7a88e2 100%);
  background-size: 100% 10px;
  box-shadow: 10px 10px 5px 0px rgba(113, 113, 113, 0.5);
}
.lined-paper .left-margin {
  height: calc(100% - 30px);
  top: 20px;
  left: 10%;
  position: absolute;
  border-left: solid rgba(255, 104, 51, 0.3) 1px;
}
.lined-paper .top-margin {
  height: calc(100% - 30px);
  top: 20px;
  position: absolute;
  width: 100%;
  top: 20px;
  border-top: double rgba(255, 104, 51, 0.3) 3px;
  border-bottom: solid rgba(255, 104, 51, 0.3) 1px;
}
.lined-paper p {
  letter-spacing: 3px;
  left: 10%;
  font-family: "Reenie Beanie", cursive;
  font-size: 28px;
  color: rgba(26, 70, 178, 0.7);
}

ul {
  list-style: none;
  padding-left: 0;
}
.card {
  display: flex;
}
.todosList {
  padding-left: 9px;
}
</style>
