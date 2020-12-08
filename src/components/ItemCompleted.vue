<template>
  <div class="task-completed">
      <img v-on:click="clearCompleted" class="task-completed-check" src="../assets/images/icon-check.svg" alt="icon check">
      <p class="task-completed-text">{{task}}</p>
  </div>
</template>

<script>
export default {
    name: 'Item',
    props: ['task', 'clearCompleted' ]
}
</script>

<style>

</style>