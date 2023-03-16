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
                <Graphic :amounts="amounts"></Graphic>
            </template>
            <template #action>
                <Action>
                    action
                </Action>
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
import Action from './Action.vue';
import Graphic from './Resume/Graphic.vue';

export default {
    components:{
        Layout,
        Header,
        Resume,
        Movements,
        Action,
        Graphic,
    },
    data(){
        return{
            label : null,
            amount : null,
            amounts : [100,200,500,200,-400,-600,-300,0,300,500],
            movements : [
            {
                id: 0,
                title: "Movimiento 1",
                description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
                amount: -1000
            },
            {
                id: 1,
                title: "Movimiento 2",
                description: "Sed euismod orci at mi ultricies, sit amet consequat metus facilisis.",
                amount: 5000
            },
            {
                id: 2,
                title: "Movimiento 3",
                description: "Nam commodo, nulla sed lobortis bibendum, nisl leo pretium mauris, at interdum velit velit ut ex.",
                amount: -6000
            },
            {
                id: 3,
                title: "Movimiento 4",
                description: "Donec malesuada tortor non ullamcorper lobortis. Vivamus in velit vel quam consequat lobortis.",
                amount: 5000
            },
        ]
        }
    },
};
</script>