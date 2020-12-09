<template>
  <div class="task-completed">
      <!-- <img v-on:click="clearCompleted" class="task-completed-check" src="../assets/images/icon-check.svg" alt="icon check">
      <p class="task-completed-text">{{task}}</p> -->
      <label class="task-completed-text" for="task" v-on:click.prevent="goActive">{{task}}
          <a name=task href="" v-on:click.prevent><img class="task-completed-check" src="../assets/images/icon-check.svg" alt="icon check completed"></a>
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