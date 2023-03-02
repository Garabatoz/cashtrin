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
                :totalAmount="'200000000'"
            >
            <template #graphic>
                graphic
            </template>
            <template #action>
                action
            </template>
        </Resume>
        </template>
        <template #movements>
            <Movements
                :movements="movements"
            />
        </template>
    </Layout>
</template>

<script>
import Layout from './Layout.vue';
import Header from './Header.vue';
import Movements from './Movements/Index.vue';
import Resume from './Resume/Index.vue';

export default {
    components:{
        Layout,
        Header,
        Resume,
        Movements,
    },
    data(){
        return{
            label : null,
            amount : null,
            movements : [
            {
                id: 0,
                title: "Movimiento 1",
                description: "",
                amount: 1000
            },
            {
                id: 1,
                title: "Movimiento 2",
                description: "",
                amount: 5000
            },
            {
                id: 2,
                title: "Movimiento 3",
                description: "",
                amount: 6000
            },
            {
                id: 3,
                title: "Movimiento 4",
                description: "",
                amount: 5000
            },
        ]
        }
    },
};
</script>