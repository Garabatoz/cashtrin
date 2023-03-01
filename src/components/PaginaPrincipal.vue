<template>
    <Layout>
        <template #header>
            <Header></Header>
        </template>
        <template #resume>
            <Resume/>
        </template>
        <template #movements>
            <Movements/>
        </template>
    </Layout>
</template>

<script>
import Layout from './Layout.vue';
import Header from './Header.vue';
import Movements from './Movements.vue';
import Resume from './Resume/Index.vue';

export default {
    components:{
        Layout,
        Header,
        Resume,
        Movements,
    },
};
</script>