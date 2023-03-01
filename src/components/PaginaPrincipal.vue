<template>
    <Layout>
        <template #header>
            <Header></Header>
        </template>
        <template #resume>
            <Resume 
                :label="label" 
                :totalLabel="'Ahorro total'" 
                :amount="amount"
                :totalAmount="'200,000.00'"
            />
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
    data(){
        this.amount = null;
        this.label = null;
    },
};
</script>