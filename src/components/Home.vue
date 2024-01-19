<script>
import IconsTrash from './Icons/Trash.vue'
import IconsDone from './Icons/Done.vue'
import IconsEdit from './Icons/Edit.vue'
import IconsClose from './Icons/Close.vue'
import IconsSun from './Icons/Sun.vue'
import IconsCancel from './Icons/Cancel.vue'
export default {
    components: {IconsTrash, IconsDone, IconsEdit,IconsClose,IconsSun, IconsCancel},
    data(){
        return{
            todos:[
                {todo:'Berangkat ke sekolah'},
                {todo:'Pulang sekolah mengerjakan tugas'},
                {todo:'Berbelanja'},
                {todo:'Pergi mengaji'},
                {todo:'Belajar untuk besok'}
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
        isReadonly(index){
            document.querySelectorAll('.todo')[index].focus()
            this.readonlySet.push(index)
            if(this.readonlySet.length > 1){
                this.readonlySet.pop()
            }
        },
        doneEdit(){
            if(this.readonlySet.length > 0){
                this.readonlySet = []
            }
        },
        cancelEdit(){
            this.doneEdit()
        },
        totalTodo(){
            this.$emit('total', this.totalData())
        },
        multiReadonly(){
            this.checkedIndex.map((index) => {
                document.querySelectorAll('.todo')[index].focus()
                return this.readonlySet.push(index)
            })
        },
        exitSelect(){
            this.checkedIndex = []
            this.readonlySet = []
        }
    }
}
</script>

<template>
    <div class="todo-lists">
        <div class="d-flex sticky-top bg-white nav-todo">
            <div v-if="checkedIndex.length > 0">
                <button class="btn btn-white fs-3" @click="exitSelect()" aria-label="Close" type="button"><IconsClose/></button>
                <button class="btn btn-white" aria-label="Trash" type="submit"><IconsTrash/></button>
                <button class="btn btn-white" @click="multiReadonly()" aria-label="Edit" type="button"><IconsEdit/></button>
                <button v-if="readonlySet.length > 0" class="btn btn-white" @click="cancelEdit()" aria-label="Cancel Edit" type="button"><IconsCancel/></button>
                <button v-if="readonlySet.length > 0" class="btn btn-white" @click="doneEdit()" aria-label="Done Edit" type="submit"><IconsDone/></button>
            </div>
            <button class="btn btn-white fs-3" aria-label="Darkmode & Lightmode" type="button"><IconsSun/></button>
        </div>
        <h1>Todo</h1>
        <p>Total todo: {{ totalData }}</p>
        <ul class="list">
            <li v-for="(todo,index) in todos" :key="todo" class="row">
                <span class="row rounded-3 p-2 border-bottom align-items-center" :class="checkedIndex.includes(index)? 'selected' : 'not-select'">
                    <div class="col-1 box"><input type="checkbox" name="select" class="selectTodo" :value="index" v-model="checkedIndex"></div>
                    <div class="col"><input type="text" name="todo" class="todo" :value="todo.todo" :readonly="readonlySet.includes(index) ? false : true" :class="readonlySet.includes(index) ? 'fw-bold' : ''"></div>
                    <div class="col-1 btnCancel" v-if="readonlySet.includes(index)"><button class="btn btn-white" @click="cancelEdit()" aria-label="Cancel Edit" type="button"><IconsCancel/></button></div>
                    <div class="col-1 btnEdit" :class="readonlySet.includes(index) ? 'hidden' : ''"><button class="btn btn-white" @click="isReadonly(index)" aria-label="Edit" type="button"><IconsEdit/></button></div>
                    <div class="col-1 btnDone" v-if="readonlySet.includes(index)"><button class="btn btn-white" @click="doneEdit()" aria-label="Done Edit" type="submit"><IconsDone/></button></div>
                    <div class="col-1 btnTrash"><button class="btn btn-white" aria-label="Trash" type="submit"><IconsTrash/></button></div>
                </span>
            </li>
        </ul>
    </div>
</template>

<style scoped>
    .todo-lists{padding: 10px 0 500px 10px;}
    .list{list-style-type: none;padding: 0;}
    .selectTodo{width: 16px;height: 16px;}
    .selected{background-color: rgb(239, 245, 253);}
    .todo{background-color: transparent;width: 100%; padding: 0 2vw;border: none;outline: none;}
    .nav-todo{width: 150%;transform:translateX(-50px) translateY(-28px);padding: 0 0 0 30px;box-shadow: rgba(0, 0, 0, 0.05) 0px 1px 2px 0px;}
    .hidden{display: none;}
    @media screen and (max-width:575px) {
        .nav-todo{transform: translateY(-24px) translateX(-50px); padding-bottom: 0px !important;}
        .btnCancel, .btnEdit, .btnDone, .btnTrash{display: none;}
        .todo-lists{padding: 0 0 800px 0;}
        .box{padding: 0 !important;}
        .todo{padding: 2vw 0!important;}
        .nav-todo{padding: 10px 35px;}
    }
</style>