<template>
    <div>
        <img class="background-image" src="../assets/images/bg-desktop-dark.jpg" alt="background image">
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
                    <item v-bind:id="index" v-bind:task="task" :goCompleted="goCompleted"></item>
                </li>
                 <li v-bind:key="index+100" v-for="(task,index) in tabCompleted">
                    <itemCompleted v-bind:id="index" v-bind:task="task" :clearCompleted="clearCompleted"></itemCompleted>
                </li>
            </ul>
            <div class="footer-app">
                <p class="status">{{tabTasks.length}} items left</p>
                <div class="footer-status">
                    <p id=all class="status-active">All</p>
                    <p id=active class="status">Active</p>
                    <p id=completed class="status">Completed</p>
                </div>
                <a id=clearCompleted class="clearCompleted" :clearCompleted="clearCompleted" href="" v-on:click.prevent="clearCompleted" >Clear Completed</a>
            </div>
        </div>
    </div>
  
</template>

<script>
import Item from './Item';
import ItemCompleted from './ItemCompleted'

const desktopBg = '../assets/images/bg-desktop-dark.jpg';

export default {
    name: 'TodoList',
    data(){
        return {
            formData: {
                task: ''
            },
            tabTasks: ['Learn Javascript', 'Learn Vue.Js'],
            tabCompleted: ['Learn PHP'],
            desktopBg: desktopBg,
        }
    },
    methods: {
        createItem: function(){
            this.tabTasks.push(this.formData.task);
            this.formData.task='';
        },
        clearCompleted: function(event){
            console.log(event.target.parentNode.id);
            this.tabCompleted.splice(0, 1000);
        },
        goCompleted: function(event){
            const element = event.target.parentNode;
            this.tabCompleted.push(element.innerText);
            this.tabTasks.splice(event.target.parentNode.id, 1,);
            
        }
    },
    components: {
        'item': Item,
        'itemCompleted': ItemCompleted,
    },

}
</script>

<style>
@import './styles/reset.css';
@import './styles/style.css';
</style>