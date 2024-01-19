<script>
import IconsTrash from './Icons/Trash.vue'
import IconsClose from './Icons/Close.vue'
import IconsSun from './Icons/Sun.vue'
export default {
    components: {IconsTrash,IconsClose,IconsSun},
    data(){
        return{
            todos:[
                {todo:'Berangkat ke sekolah'},
                {todo:'Pulang sekolah mengerjakan tugas'},
                {todo:'Berbelanja'},
            ],
            checkedIndex: [],
            readonlySet: []
        }
    },
    computed: {
        totalData(){
            return this.todos.length
        }
    },
    methods: {
        totalTodo(){
            this.$emit('total', this.totalData())
        },
        exitSelect(){
            this.checkedIndex = []
            this.readonlySet = []
        }
    },
}
</script>

<template>
    <div class="trash-list">
        <div class="d-flex sticky-top bg-white nav-todo">
            <div v-if="checkedIndex.length > 0">
                <button class="btn btn-white fs-3" @click="exitSelect()"><IconsClose/></button>
                <button class="btn btn-white"><IconsTrash/></button>
            </div>
            <button class="btn btn-white fs-3"><IconsSun/></button>
        </div>
        <h1>Trash</h1>
        <p>Total trash: {{ totalData }}</p>
        <ul class="list">
            <li v-for="(todo,index) in todos" :key="todo" class="row">
                <span class="row rounded-3 p-2 border-bottom flex align-items-center" :class="checkedIndex.includes(index)? 'selected' : 'not-select'">
                    <div class="col-1 box"><input type="checkbox" name="select" id="selectTodo" :value="index" v-model="checkedIndex"></div>
                    <div class="col"><input type="text" name="todo" id="todo" :value="todo.todo" :readonly="readonlySet.includes(index) ? false : true" :class="readonlySet.includes(index) ? 'fw-bold' : ''"></div>
                    <div class="col-1 btnTrash"><button class="btn btn-white"><IconsTrash/></button></div>
                </span>
            </li>
        </ul>
    </div>
</template>

<style scoped>
    .trash-list{padding: 10px 0 500px 10px;}
    .list{list-style-type: none;padding: 0;}
    #selectTodo{width: 16px;height: 16px;}
    .selected{background-color: rgb(239, 245, 253);}
    #todo{background-color: transparent;width: 100%; padding: 0 2vw;border: none;outline: none;}
    .nav-todo{width: 150%;transform:translateX(-50px) translateY(-28px);padding: 0 0 0 30px;box-shadow: rgba(0, 0, 0, 0.05) 0px 1px 2px 0px;}
    .hidden{display: none;}
    @media screen and (max-width:575px) {
        .nav-todo{transform: translateY(-24px) translateX(-50px); padding-bottom: 0px !important;}
        .btnCancel, .btnEdit, .btnDone, .btnTrash{display: none;}
        .trash-list{padding: 0 0 800px 0;}
        .box{padding: 0 !important;}
        #todo{padding: 2vw 0!important;}
        .nav-todo{padding: 10px 35px;}
        .box{padding: 0 !important;}
    }
</style>