<template>
    <div>
        <div v-if="darkmode" class="task-completed">
            <label class="task-completed-text">{{task}}
                <img name=task class="task-completed-check" src="../assets/images/icon-check.svg" alt="icon check completed" href="" v-on:click.prevent="goActive">
            </label>
        </div>
        <div v-else class="task-completed task-completed-light">
            <label class="task-completed-text">{{task}}
                <img name=task class="task-completed-check" src="../assets/images/icon-check.svg" alt="icon check completed" href="" v-on:click.prevent="goActive">
            </label>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Item',
    props: ['task', 'clearCompleted', 'goActive', 'darkmode' ]
}
</script>

<style>

</style>