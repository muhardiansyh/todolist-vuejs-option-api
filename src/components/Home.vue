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
                {
                    todo:'Berangkat ke sekolah',
                    time: '08:00'
                },
                {
                    todo:'Pulang sekolah mengerjakan tugas',
                    time: '12:00'
                },
                {
                    todo:'Berbelanja',
                    time: '14:00'
                },
                {
                    todo:'Pergi mengaji',
                    time: '16:00'
                },
                {
                    todo:'Belajar untuk besok',
                    time: '18:00'
                }
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
            document.querySelectorAll('#todo')[index].focus()
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
        }
    }
}
</script>

<template>
    <ol class="todo-lists">
        <div class="d-flex sticky-top bg-white nav-todo">
            <div v-if="checkedIndex.length > 0">
                <button class="btn btn-white fs-3"><IconsClose/></button>
                <button class="btn btn-white"><IconsTrash/></button>
            </div>
            <button class="btn btn-white fs-3"><IconsSun/></button>
        </div>
        <p>Total todo: {{ totalData }}</p>
        <li v-for="(todo,index) in todos" :key="todo" class="row">
            <span class="row rounded-3 p-2 border-bottom flex align-items-center" :class="checkedIndex.includes(index)? 'selected' : 'not-select'">
                <div class="col-1"><input type="checkbox" name="select" id="selectTodo" :value="index" v-model="checkedIndex"></div>
                <div class="col"><input type="text" name="todo" id="todo" :value="todo.todo" :readonly="readonlySet.includes(index) ? false : true" :class="readonlySet.includes(index) ? 'fw-bold' : ''"></div>
                <div class="col-1" v-if="readonlySet.includes(index)"><button class="btn btn-white" @click="cancelEdit()"><IconsCancel/></button></div>
                <div class="col-1" :class="readonlySet.includes(index) ? 'hidden' : ''"><button class="btn btn-white" @click="isReadonly(index)"><IconsEdit/></button></div>
                <div class="col-1" v-if="readonlySet.includes(index)"><button class="btn btn-white" @click="doneEdit()"><IconsDone/></button></div>
                <div class="col-1"><button class="btn btn-white"><IconsTrash/></button></div>
                <small class="col-1">{{ todo.time }}</small>
            </span>
        </li>
    </ol>
</template>

<style scoped>
    .todo-lists{padding-bottom: 500px;}
    #selectTodo{width: 16px;height: 16px;}
    .selected{background-color: rgb(239, 245, 253);}
    #todo{background-color: transparent;width: 100%; padding: 0 2vw;border: none;outline: none;}
    .nav-todo{width: 150%;transform:translateX(-50px) translateY(-16px);padding: 0 0 0 30px;box-shadow: rgba(0, 0, 0, 0.05) 0px 1px 2px 0px;}
    .hidden{display: none;}
</style>