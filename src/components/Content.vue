<script>
import IconsPlus from './Icons/Plus.vue'
import IconsSend from './Icons/Send.vue'
import Home from './Home.vue'
import Trash from './Trash.vue'
import About from './About.vue'
import InputTodo from './InputTodo.vue'
export default {
    components: {IconsPlus,IconsSend,InputTodo,Home,Trash,About},
    data(){
        return{
            navbarMenu: ['Home', 'Trash', 'About'],
            currentTab: 'Home'
        }
    },
    computed:{
        currentTabComponent(){
            return this.currentTab.toLowerCase()
        }
    },
    methods:{

    }
}
</script>

<template>
    <div class="row">
        <div class="col-2">
            <div class="row gap-3">
                <div class="col">
                    <h1 class="fs-3 text-secondary mb-3 fw-bold">TodoList App</h1>
                    <button class="btn btn-primary px-4 py-2 rounded-3 fs-5">Todo<IconsPlus/></button>
                </div>
                <div class="col">
                    <ul class="list-group">
                        <li v-for="item in navbarMenu" :key="item" class="list-group-item bg-transparent mt-2 border border-0"><a href="#" class="text-decoration-none rounded-5" :class="{active: currentTab === item}" @click="currentTab = item">{{ item }}</a></li>
                    </ul>
                </div>
            </div>
        </div>
        <div class="col">
            <div class="row">
                <div class="col d-flex justify-content-center flex-column">
                    <InputTodo/>
                    <div class="p-3 bg-white rounded-4 overflow-auto todos-content z-1">
                        <component :is="currentTabComponent"></component>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
    a{padding: .5vw 15vw .5vw 1vw;}
    a:hover{background-color: white;}
    .active{background-color: white;}
    .todos-content{height: 1000px;}
</style>