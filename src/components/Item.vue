<template>
  <div class="task">
      <!-- <a class="task-check" for=task href="" v-on:click.prevent></a>
      <a class="task-text" href="" name=task v-on:click.prevent="goCompleted">{{task}} </a> -->
      <label class="task-text">{{task}}
          <a class="task-check" href="" v-on:click.prevent="goCompleted"></a>
      </label>
  </div>
</template>

<script>
export default {
    name: 'Item',
    props: ['task', 'goCompleted' ]
}
</script>

<style>

</style>