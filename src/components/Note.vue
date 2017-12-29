<template>
  <div>
    <div>
      <input v-model.trim='newNote' type='text'/>
      <button @click="createNote">Add</button>
    </div>
    <div v-for='note in notes'>
      <input type='checkbox' />
      <span>{{note}}</span>
      <button>delete</button>
    </div>
  </div>
</template>

<script>
  export default {
    data: () => ({
      newNote: '',
      notes: []
    }),
    methods: {
      createNote () {
        if (this.newNote !== "") {
          this.notes.push(this.newNote)
          this.newNote = ''
        }
      }
    }
  }
</script>
