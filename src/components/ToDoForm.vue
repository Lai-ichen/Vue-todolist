<template>
    <form @submit.prevent="onSubmit">
      <h2 class="label-wrapper">
      <label for="new-todo-input" class="label__lg"> What needs to be done? </label>
      </h2>
      <input
        type="text"
        id="new-todo-input"
        name="new-todo"
        autocomplete="off" 
        v-model.lazy.trim="label"
        class="input__lg" />
      <button type="submit" class="btn btn__primary btn__lg">Add</button>
    </form>
  </template>

<script>
  export default {
    methods: {
      onSubmit() {
      if(this.label === ""){
        return;
      }
      //console.log('Label value: ', this.label);
      this.$emit("todo-added", this.label);//If the label value is empty, let's not emit the todo-added event.
      this.label = "";//click the "Add" button, the "new-todo-input" will clear itself.
      },
  },
  data() {
    return {
      label: "",
    };
  },
};

</script>