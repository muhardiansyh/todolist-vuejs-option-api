<template>
    <div class="layout row pt-5 px-xl-5 px-lg-5 px-md-4 px-sm-4">
        <div class="col p-xl-5 p-lg-5 px-md-4 py-md-5 py-sm-4 rounded-5">
            <slot name="content"/>
        </div>
    </div>
</template>

<style scoped>
    .layout{width: 100%;position: fixed;}
    .col{width: 100%;height: 100%;background-color: rgb(245, 245, 245);}
    @media screen and (max-width:575px) {
        .layout{padding: 0px 0px 0 0px !important;}
        .col{padding: 24px 0 0 0; border-radius: 0 !important;}
    }
</style>