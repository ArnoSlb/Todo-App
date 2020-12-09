<template>
  <div class="task-completed">
      <!-- <img v-on:click="clearCompleted" class="task-completed-check" src="../assets/images/icon-check.svg" alt="icon check">
      <p class="task-completed-text">{{task}}</p> -->
      <label class="task-completed-text">{{task}}
          <img name=task class="task-completed-check" src="../assets/images/icon-check.svg" alt="icon check completed" href="" v-on:click.prevent="goActive">
      </label>
  </div>
</template>

<script>
export default {
    name: 'Item',
    props: ['task', 'clearCompleted', 'goActive' ]
}
</script>

<style>

</style>