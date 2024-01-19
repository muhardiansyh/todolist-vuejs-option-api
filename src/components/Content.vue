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
    <div class="row content">
        <aside class="col-2">
            <div class="gap-3 menu">
                <div class="menu-title">
                    <h1 class="fs-3 text-secondary fw-bold title mb-xl-3 mb-lg-3">TodoList App</h1>
                    <button class="btn btn-primary px-4 py-2 rounded-3 fs-5">Todo<IconsPlus/></button>
                </div>
                <nav class="nav-menu">
                    <ul>
                        <li v-for="item in navbarMenu" :key="item" class="bg-transparent mt-3 me-1">
                            <button class="rounded-5 btn-menu border border-0 text-primary" :class="{active: currentTab === item}" @click="currentTab = item">{{ item }}</button>
                        </li>
                    </ul>
                </nav>
            </div>
        </aside>
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
    .btn-menu{padding: .5vw 15vw .5vw 1vw; background-color: transparent;}
    .btn-menu:hover{background-color: white;}
    .active{background-color: white;}
    .todos-content{height: 1000px;}
    .menu{display: flex; flex-direction: column;}
    .nav-menu ul{list-style: none;}

    @media screen and (min-width:768px) and (max-width:1023px) {
        .content{display: flex; flex-direction: column;gap: 50px;}
        aside{width: 100%;}
        .menu{flex-direction: row;align-items: center;justify-content: start;}
        .nav-menu ul{display: flex;}
        .btn-menu{padding: .5vw 3vw .5vw 3vw;}
        .menu-title{display: flex; gap: 24px; align-items: center;}
    }
    @media screen and (max-width:767px){
        .content{display: flex; flex-direction: column;gap: 50px;}
        aside{width: 100%;}
        .menu{flex-direction: column;align-items: start;justify-content: start;}
        .nav-menu ul{display: flex;}
        .btn-menu{padding: .5vw 3vw .5vw 3vw;}
        .menu-title{display: flex; gap: 24px; align-items: center;}
        .menu-title h1{margin-left: 24px !important;}
    }
    @media screen and (max-width:575px) {
        .todos-content{overflow-x: hidden !important;}
        .nav-menu ul{padding: 0 0 0 16px !important;}
        .content{gap: 40px !important;}
        .menu-title h1{margin-left: 18px !important;}
    }
</style>