<template>
  <div>
    <header v-if="isEditing">
      <input type="text" v-model="name" />
      <button v-on:click.prevent="upEdit(this.name)">Modificar</button>
    </header>
    <header v-else>
      <input type="text" v-model="name" />
      <button v-on:click.prevent="addTask">Adicionar</button>
    </header>
    <div class="content-tasks">
      <div class="task" v-for="(task, i) in tasks">
        <div class="title">
          <h4>{{ task.name }}</h4>
        </div>
        <div class="icones">
          <i
            class="bx bxs-edit"
            v-on:click.prevent="editTask(i, task.name)"
          ></i>
          <i class="bx bx-trash" v-on:click.prevent="removeTask(i)"></i>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FormTask",
  data() {
    return {
      isEditing: false,
      indexSelect: null,
      tasks: [],
      name: "",
    };
  },
  methods: {
    addTask() {
      if (this.name.trim() === "") {
        return;
      }
      this.tasks.push({
        name: this.name,
      });
      this.name = "";
    },

    removeTask(i) {
      this.tasks.splice(i, 1);
    },

    editTask(i, name) {
      this.name = name;
      this.isEditing = true;
      this.indexSelect = i;
    },

    upEdit(i, name) {
      this.tasks.splice(i, 1);
      this.tasks.push({
        name: this.name,
      });
      this.isEditing = false;
      this.name = "";
    },
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
}

input {
  width: 75%;
  padding: 8px 15px;
  border-radius: 5px;
  background-color: #fff;
  border: 1px solid rgb(245, 245, 245);
  outline: none;
}

button {
  width: 24%;
  background-color: rgb(12, 186, 56);
  color: white;
  border: 1px solid rgb(0, 149, 37);
  cursor: pointer;
  border-radius: 5px;
  font-weight: 600;
  text-transform: uppercase;
  font-size: 10px;
}

.content-tasks {
  margin-top: 30px;
}

.task {
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: #fff;
  background-color: rgba(213, 213, 213, 0.459);
  padding: 15px;
  border-radius: 5px;
  margin: 10px 0;
}

.title {
  width: 85%;
  overflow: hidden;
  display: flex;
  flex-wrap: wrap;
}

.icones {
  width: 60px;
}
.bx {
  padding: 5px;
  border-radius: 5px;
  cursor: pointer;
}

.bxs-edit:hover {
  background-color: rgb(208, 208, 208);
}

.bx-trash:hover {
  background-color: rgb(255, 0, 0);
}

@media (min-width: 930px) {
  input {
    width: 80%;
  }

  button {
    width: 19%;
    font-size: 11px;
  }
}
</style>
