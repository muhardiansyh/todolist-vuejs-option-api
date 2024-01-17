<script>
import IconsSend from './Icons/Send.vue'
export default {
    components: {IconsSend},
    data(){
        return{

        }
    }
}
</script>

<template>
    <div class="row">
        <span class="col">
            <input type="text" name="activity" id="activity" class="border-bottom mb-3" placeholder="Write your todo">
        </span>
        <span class="col">
            <input type="time" name="time" id="time-activity" class="border border-1 rounded-4 me-3">
            <button class="btn btn-primary rounded-5 fw-bold" type="button">Add todo &nbsp; <IconsSend/></button>
        </span>
    </div> 
</template>

<style scoped>
    #activity{padding: 1vw 2vw;border: none;outline: none;width: 100%;background-color: whitesmoke;}
    ::placeholder{color: lightslategray;font-weight: bold;}
    #time-activity{outline: none;padding: 1vw 2vw;background-color: whitesmoke;cursor: pointer;color: lightslategray;}
    #time-activity::-webkit-calendar-picker-indicator{cursor: pointer;}
</style>