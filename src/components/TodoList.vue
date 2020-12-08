<template>
    <div>
        <img src="../assets/images/bg-desktop-dark.jpg" alt="">
        <div>{{desktopBg}}</div>
        <img :src="desktopBg" alt="">
        <div class="todo-app">
            <div class="todo-app-header">
                <h1>TODO</h1>
                <img class="icon-mode" src="../assets/images/icon-sun.svg" alt="">
            </div>
                <input v-model="formData.task" v-on:keyup.enter="createItem" type="text" id="action" placeholder="Create a new todo...">
            <ul>
                <li v-bind:key="index" v-for="(task,index) in tabTasks">
                    <item v-bind:task="task"></item>
                </li>
            </ul>
            <div class="footer-app">
                <p>{{tabTasks.length}} items left</p>
                <div class="footer-status">
                    <p class="status-active">All</p>
                    <p class="status">Active</p>
                    <p class="status">Completed</p>
                </div>
                <p>Clear Completed</p>
            </div>
        </div>
    </div>
  
</template>

<script>
import Item from './Item';

const desktopBg = '../assets/images/bg-desktop-dark.jpg';

export default {
    name: 'TodoList',
    data(){
        return {
            formData: {
                task: ''
            },
            tabTasks: ['Learn Javascript', 'Learn Vue.Js'],
            desktopBg: desktopBg,
        }
    },
    methods: {
        createItem: function(){
            this.tabTasks.push(this.formData.task)
            this.formData.task='';
        }
    },
    components: {
        'item': Item
    },

}
</script>

<style>
@import './styles/reset.css';
@import './styles/style.css';
</style>