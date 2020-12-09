<template>
    <div>
        <div v-if="darkmode" class="task">
            <label class="task-text">{{task}}
                <a class="task-check" href="" v-on:click.prevent="goCompleted"></a>
            </label>
        </div>
        <div v-else class="task task-light ">
            <label class="task-text task-text-light">{{task}}
                <a class="task-check" href="" v-on:click.prevent="goCompleted"></a>
            </label>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Item',
    props: ['task', 'goCompleted', 'switchMode', 'darkmode' ]
}
</script>

<style>

</style>