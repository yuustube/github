<template>
  <div class='ui centered card'>
    <!-- // Todo shown when we are not in editing mode. -->
    <div class="content" v-show="!isEditing">
      <div class='header'>
          {{ todoItems }}
      </div>
      <div class='extra content'>
        <span class='right floated edit icon' v-on:click="showForm">
          <i class='edit icon big'></i>
        </span>
      </div>
    </div>
    <!-- // form is visible when we are in editing mode -->
    <div class="content" v-show="isEditing">
      <div class="ui form">
        <div class="field">
          <label>Title</label>
          <input type="text" v-model="todo.title" >
        </div>
        <div class="ui two button attached buttons">
          <button class="ui basic blue button" v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>
    <div class="ui bottom attached green basic button" v-show="!isEditing && todo.done" disabled>
        Completed
    </div>
    <div class="ui bottom attached red basic button" v-show="!isEditing && !todo.done" v-on:click="completeTodo(todo)">
        Pending
    </div>
  </div>
</template>

<script>
export default {
  props: ["propsdata"],
  data() {
    return {
      isEditing: false
    };
  },
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
  }
};
</script>

<style lang="scss" scoped>
.button[disabled] {
  cursor: not-allowed;
}
i {
  cursor: pointer;
}
</style>
