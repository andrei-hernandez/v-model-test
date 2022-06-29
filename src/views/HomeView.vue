<template>
  <form @submit.prevent="onSubmit">
    <input
      type="text"
      v-model.trim="task.name"
      class="form-control my-2"
      placeholder="Enter a name"
    />
    <div class="form-check form-check-inline">
      <input
        type="checkbox"
        id="check-1"
        class="form-check-input"
        v-model="task.categories"
        value="javascript"
      />
      <label class="form-check-label" for="check-1">Javascript</label>
    </div>
    <div class="form-check form-check-inline">
      <input
        type="checkbox"
        id="check-2"
        class="form-check-input"
        v-model="task.categories"
        value="node js"
      />
      <label class="form-check-label" for="check-2">Node.js</label>
    </div>
    <div class="mt-2">
      <div class="form-check form-check-inline">
        <input
          type="radio"
          id="radio-1"
          class="form-check-input"
          v-model="task.state"
          value="urgent"
        />
        <label class="form-check-label" for="check-1">Urgent</label>
      </div>
      <div class="form-check form-check-inline">
        <input
          type="radio"
          id="radio-2"
          class="form-check-input"
          v-model="task.state"
          value="chill"
        />
        <label class="form-check-label" for="check-2">Chill</label>
      </div>
    </div>
    <div class="mt-2">
      <input type="number" class="form-control" v-model.number="task.number" />
    </div>

    <button
      type="submit"
      :disabled="isDisabledSubmit"
      class="btn btn-dark mt-2"
    >
      Submit
    </button>
  </form>
  <hr />
  <p>
    {{ task }}
  </p>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

interface Task {
  name: string
  categories: Array<string>
  state: string
  number: number
}

export default defineComponent({
  name: 'HomeView',
  components: {},
  data () {
    return {
      task: {
        name: '',
        categories: [],
        state: '',
        number: 0
      } as Task
    }
  },
  methods: {
    onSubmit () {
      if (this.task.name.trim() === '') {
        console.log('Name is empty')
        return
      }
      console.log(this.task)
      this.task = {
        name: '',
        categories: [],
        state: '',
        number: 0
      }
    }
  },
  computed: {
    isDisabledSubmit (): boolean {
      return this.task.name.trim() === ''
    }
  }
})
</script>
