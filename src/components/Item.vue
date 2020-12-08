<template>
  <div class="task">
      <img class="task-check" src="../assets/images/icon-check.svg" alt="icon check">
      <p class="task-text">{{task}}</p>
  </div>
</template>

<script>
export default {
    name: 'Item',
    props: ['task', 'completed' ]
}
</script>

<style>

</style>