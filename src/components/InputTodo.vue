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
    <div class="input-area">
        <span class="input-todo">
            <input type="text" name="activity" id="activity" class="border-bottom mb-3" placeholder="Write your todo">
        </span>
        <span class="input-btn">
            <button class="btn btn-primary rounded-5 fw-bold" type="button">Add todo &nbsp; <IconsSend/></button>
        </span>
    </div> 
</template>

<style scoped>
    #activity{padding: 1vw 2vw;border: none;outline: none;width: 45vw;background-color: whitesmoke;}
    ::placeholder{color: lightslategray;font-weight: bold;}
    .input-area{display: flex;justify-content: start; gap: 24px;}

    @media screen and (min-width:768px) and (max-width:1023px) {
        #activity{width: 55vw;}
    }
    @media screen and (max-width:767px) {
        #activity{width: 50vw;}
    }
    @media screen and (max-width:575px) {
        #activity{width: 40vw;margin-bottom: 24px !important;}
        .input-btn{width: 100vw;}
    }
</style>