<template>
  <q-page class="bg-green-3 column">
    <q-list 
    separator
    class="q-mx-sm"
    >
      <q-item
        clickable
        @click="task.done = !task.done"
        class="shadow-6 q-my-sm"
        :class="{ 'done bg-yellow-3': task.done }"
        v-ripple
        v-for="task, index in tasks"
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
        <q-item-section
        v-if="task.done"
        side
        >
          <q-btn 
          dense flat round
          @click.stop="deleteTask(index)"
          color="red" 
          icon="delete" />
        </q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
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
      this.tasks.splice(index, 1)
    }
  }
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
