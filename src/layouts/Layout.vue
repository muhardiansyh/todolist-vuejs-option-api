<template>
    <div class="layout row p-5 position-fixed">
        <div class="col p-5 rounded-5">
            <slot name="content"/>
        </div>
    </div>
</template>

<style scoped>
    .layout{width: 100%;}
    .col{width: 100%;height: 100%;background-color: rgb(245, 245, 245);}
</style>