<template>
    <div>
        <img class="background-image" src="../assets/images/bg-desktop-dark.jpg" alt="background image">
        <!-- <div>{{desktopBg}}</div>
        <img :src="desktopBg" alt=""> -->
        <div class="todo-app">
            <div class="todo-app-header">
                <h1>TODO</h1>
                <img class="icon-mode" src="../assets/images/icon-sun.svg" alt="">
            </div>
                <input v-model="formData.task" v-on:keyup.enter="createItem" type="text" id="action" placeholder="Create a new todo...">
            <div v-if="filter === 'all'">
                <ul>
                    <li v-bind:key="task" v-for="(task,index) in tabTasks">
                        <item 
                            v-bind:id="index" 
                            v-bind:task="task" 
                            :goCompleted="goCompleted"
                        ></item>
                    </li>
                    <li v-bind:key="task" v-for="(task,index) in tabCompleted">
                        <itemCompleted 
                            v-bind:id="index" 
                            v-bind:task="task" 
                            :clearCompleted="clearCompleted" 
                            :goActive="goActive"
                        ></itemCompleted>
                    </li>
                </ul>
            </div>
            <div v-if="filter === 'active'">
                <ul>
                    <li v-bind:key="task" v-for="(task,index) in tabTasks">
                        <item 
                            v-bind:id="index" 
                            v-bind:task="task" 
                            :goCompleted="goCompleted"
                        ></item>
                    </li>
                </ul>
            </div>
            <div v-if="filter === 'completed'">
                <ul>
                    <li v-bind:key="task" v-for="(task,index) in tabCompleted">
                        <itemCompleted 
                            v-bind:id="index" 
                            v-bind:task="task" 
                            :clearCompleted="clearCompleted" 
                            :goActive="goActive"
                        ></itemCompleted>
                    </li>
                </ul>
            </div>
            <div class="footer-app">
                <p class="items">{{tabTasks.length}} task(s) left to do</p>
                <div class="footer-status">
                    <div v-if="filter === 'all'">
                        <a id=all class="status-active" href="" v-on:click.prevent="filterAll">All</a>
                        <a id=active class="status" href="" v-on:click.prevent="filterActive">Active</a>
                        <a id=completed class="status" href="" v-on:click.prevent="filterCompleted">Completed</a>
                    </div>
                    <div v-if="filter === 'active'">
                        <a id=all class="status" href="" v-on:click.prevent="filterAll">All</a>
                        <a id=active class="status-active" href="" v-on:click.prevent="filterActive">Active</a>
                        <a id=completed class="status" href="" v-on:click.prevent="filterCompleted">Completed</a>
                    </div>
                    <div v-if="filter === 'completed'">
                        <a id=all class="status" href="" v-on:click.prevent="filterAll">All</a>
                        <a id=active class="status" href="" v-on:click.prevent="filterActive">Active</a>
                        <a id=completed class="status-active" href="" v-on:click.prevent="filterCompleted">Completed</a>
                    </div>
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
            tabTasks: [],
            tabCompleted: [],
            desktopBg: desktopBg,
            filter: "all",
        }
    },
    // created(){
    //     console.log(this.tabTasks)
    //     console.log(this.tabCompleted)
    // },
    // updated(){
    //     console.log(this.tabTasks)
    //     // console.log(this.tabCompleted)
    // },
    methods: {
        createItem: function(){
            this.tabTasks.push(this.formData.task);
            this.formData.task='';
        },
        clearCompleted: function(){
            // console.log(event.target.parentNode.id);
            this.tabCompleted.splice(0, 1000);
        },
        goCompleted: function(event){
            // console.log('goCompleted', event.target.parentNode.parentNode.id);
            // console.log('goCompleted',event.target.parentNode.innerText);
            this.tabTasks.splice(event.target.parentNode.parentNode.id, 1,);
            this.tabCompleted.push(event.target.parentNode.innerText);
            
        },
        goActive: function(event){
            // console.log('goActive', event.target.parentNode.parentNode.id);
            // console.log('goActive', event.target.parentNode.innerText);
            this.tabCompleted.splice(event.target.parentNode.parentNode.id, 1);
            this.tabTasks.push(event.target.parentNode.innerText);

        },
        filterAll: function(){
            // console.log('je passe dans filter All');
            this.filter = "all";
            // console.log(this.filter);
        },
        filterActive: function(){
            // console.log('je passe dans filter Active');
            this.filter = "active";
            // console.log(this.filter);
        },
        filterCompleted: function(){
            // console.log('je passe dans filter Completed');
            this.filter = "completed";
            // console.log(this.filter);
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