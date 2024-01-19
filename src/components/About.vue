<script>
import IconsSun from './Icons/Sun.vue'
export default {
    components: {IconsSun},
}
</script>

<template>
    <div class="about">
        <div class="d-flex align-items-center sticky-top bg-white head-about">
            <button class="btn btn-white fs-3"><IconsSun/></button>
        </div>
        <h1>About</h1>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt dolor quis ratione itaque? Qui facere reprehenderit, hic vitae rerum consequatur harum, voluptas aspernatur architecto dolorem, laborum ducimus expedita recusandae. Aliquid. Lorem ipsum dolor sit amet consectetur adipisicing elit. Possimus eum mollitia hic corporis aut temporibus exercitationem a reiciendis repellat dolore maxime consequuntur molestias impedit dignissimos, id asperiores facilis in aperiam?</p>
    </div>
</template>

<style scoped>
    .about{padding: 10px 0 500px 10px;}
    #selectTodo{width: 16px;height: 16px;}
    .selected{background-color: rgb(239, 245, 253);}
    #todo{background-color: transparent;width: 100%; padding: 0 2vw;border: none;outline: none;}
    .head-about{width: 150%; transform:translateX(-50px) translateY(-28px);padding: 0 0 0 30px;box-shadow: rgba(0, 0, 0, 0.05) 0px 1px 2px 0px;}
    .hidden{display: none;}
    @media screen and (max-width:575px) {
        .head-about{transform: translateY(-24px) translateX(-50px); padding-bottom: 0px !important;}
        .btnCancel, .btnEdit, .btnDone, .btnTrash{display: none;}
        .about{padding: 0 0 800px 0;}
        small{display: none;}
        .box{padding: 0 !important;}
        #todo{padding: 2vw 0!important;}
        .head-about{padding: 10px 35px;}
    }
</style>