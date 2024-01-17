<script>
import Layout from './layouts/Layout.vue'
import Content from './components/Content.vue';
export default {
    components: { Layout, Content }
}
</script>

<template>
    <Layout>
        <template #content>
            <Content/>
        </template>
    </Layout>
</template>