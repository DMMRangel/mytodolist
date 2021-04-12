<template>
  <div class="app">
    <v-app>
      <v-container>
        <v-main>
          <v-toolbar dark color="green">
            <v-toolbar-title>Lista de Tarefas</v-toolbar-title>
          </v-toolbar>

          <div>
            <v-text-field
              placeholder="Digite uma tarefa..."
              v-model="task"
              @keyup.enter="capturarTask()"
            ></v-text-field>
            <v-btn class="my-5" @click="capturarTask()" dark color="success">
              Adicionar</v-btn
            >
          </div>

          <v-divider></v-divider>

          <v-list-item-group
            multiple
            color="success"
            active-class="">
            <v-list-item
              v-for="(task, i) in tasks"
              :key="i">
              <template v-slot:default="{ active }">
                <v-list-item-content>
                  {{ task }}
                </v-list-item-content>
                <v-list-item-action>
                  <v-checkbox
                    color="success"
                    :input-value="active"></v-checkbox>
                </v-list-item-action>
              </template>
            </v-list-item>
          </v-list-item-group>
        </v-main>
      </v-container>
    </v-app>
  </div>
</template>

<script>
export default {
  name: "App",

  components: {
    //
  },

  data: () => ({
    task: "",
    tasks: [],
  }),

  methods: {
    capturarTask() {
      this.tasks.push(this.task);
      console.log(`Tarefa adicionada: ${this.task}.`);
      console.log(this.tasks);
      this.task = "";
    },
  },
};
</script>
