<template>
  <q-page class="bg-green-3 column">
    <div class="row q-pa-sm bg-primary">
      <q-input
        filled square dense
        @keyup.enter="addTask"
        class="col"
        bg-color="white"
        v-model="newTask"
        placeholder="To do..."
      >
        <template v-slot:append>
          <q-icon @click="addTask" round dense flat name="send" />
        </template>
      </q-input>
    </div>

    <q-list separator class="q-mx-sm">
      <q-item
        clickable
        @click="task.done = !task.done"
        class="shadow-6 q-my-sm"
        :class="{ 'done bg-yellow-3': task.done }"
        v-ripple
        v-for="(task, index) in tasks"
        :key="task.title"
      >
        <q-item-section avatar>
          <q-checkbox
            class="no-pointer-events"
            v-model="task.done"
            val="teal"
            color="cyan"
          />
        </q-item-section>
        <q-item-section>
          <q-item-label> {{ task.title }} </q-item-label>
        </q-item-section>
        <q-item-section v-if="task.done" side>
          <q-btn
            dense
            flat
            round
            @click.stop="deleteTask(index)"
            color="red"
            icon="delete"
          />
        </q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: [
        {
          title: "hello world",
          done: false,
        },
        {
          title: "2",
          done: false,
        },
        {
          title: "3",
          done: false,
        },
      ],
    };
  },
  methods: {
    deleteTask(index) {
      this.$q
        .dialog({
          dark: true,
          title: "Delete",
          message: "Are you sure you want to delete?",
          cancel: true,
          persistent: true,
        })
        .onOk(() => {
          this.tasks.splice(index, 1);
          this.$q.notify("Deleted");
        });
    },
    addTask() {
      this.tasks.push({
        title: this.newTask,
        done: false
      }) 
      this.newTask = ''
    },
  },
};
</script>

<style lang="scss">
.done {
  .q-item__label {
    text-decoration: line-through;
    color: grey;
  }
}
</style>
