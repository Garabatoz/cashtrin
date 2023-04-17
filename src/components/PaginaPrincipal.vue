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
                :totalAmount="totalAmount"
            >
            <template #graphic>
                <Graphic :amounts="amounts" @select="select"></Graphic>
            </template>
            <template #action>
                <Action @create="create"/>
            </template>
        </Resume>
        </template>
        <template #movements>
            <Movements
                :movements="movements"
                @remove="remove"
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
            movements : [
            /* {
                id: 0,
                title: "Movimiento 1",
                description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
                amount: -1000,
                time: new Date("12-04-2023")
            },
            {
                id: 1,
                title: "Movimiento 2",
                description: "Sed euismod orci at mi ultricies, sit amet consequat metus facilisis.",
                amount: 5000,
                time: new Date("04-04-2023")
            },
            {
                id: 2,
                title: "Movimiento 3",
                description: "Nam commodo, nulla sed lobortis bibendum, nisl leo pretium mauris, at interdum velit velit ut ex.",
                amount: -6000,
                time: new Date("04-04-2023")
            },
            {
                id: 3,
                title: "Movimiento 4",
                description: "Donec malesuada tortor non ullamcorper lobortis. Vivamus in velit vel quam consequat lobortis.",
                amount: 5000,
                time: new Date("04-04-2023")
            }, */
        ]
        }
    },
    computed:{
        amounts(){
            const lastDays = this.movements
            .filter(m => {
                const today = new Date();
                const oldDate = today.setDate(today.getDate() - 30)

                return m.time > oldDate
            })
            .map(m => m.amount)
            return lastDays.map((m,i) => {
                const lastMovements = lastDays.slice(0,i+1);

                return lastMovements.reduce((suma, movement)=>{
                    return suma + movement
                }, 0)
            });
        },
        totalAmount(){
            return this.movements.reduce((suma,m) =>{
                return suma + m.amount
            },0)
        }
    },
    methods: {
        mounted() {
            const movements = JSON.parse(localStorage.getItem("movements"));
            console.log(movements);
            if (Array.isArray(movements)) {
            this.movements = movements.map(m => {
                return { ...m, time: new Date(m.time) };
            });
            }
        },
        create(movement){
            this.movements.push(movement);
            this.save();
        },
        remove(id){
            const index = this.movements.findIndex(m => m.id === id)
            this.movements.splice(index,1);
            this.save();
        },
        save(){
            localStorage.setItem("movements", JSON.stringify(this.movements));
        },
        select(el){
            console.log(el);
            this.amount = el;
        }
    }
};
</script>