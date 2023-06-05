<template>
    <Layout>
        <template #header>
            <Header></Header>
        </template>
        <template #resume>
            <Resume 
                :label="'Total savings'"
                :total-amount="150000"
                :amount="amount"
            >
                <template #graphic>
                    <Graphic :amounts="amounts"/>
                </template>
                 <template  #action>
                    <ActionButton @create="create"/>
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
import LayoutComponent from './LayoutComponent'
import HeaderComponent from './HeaderComponent'
import Resume from './resume/index.vue'
import Movements from './Movements/index.vue'
import ActionButton from './ActionButton.vue'
import Graphic from './Graphic.vue'


export default {
    components: {
    Layout: LayoutComponent,
    Header: HeaderComponent,
    Resume,
    Movements,
    ActionButton,
    Graphic
},
    data() {
        return {
            amount: null,
            movements: [
                {
                    id: 0,
                    title: "Movimiento 1",
                    description: "Lorem ipsum dolor sit amet",
                    amount: 100,
                    time: new Date("06-01-2023"),
                },
                {
                    id: 1,
                    title: "Movimiento 2",
                    description: "Lorem ipsum dolor sit amet",
                    amount: 200,
                    time: new Date("06-01-2023"),
                },
                {
                    id: 2,
                    title: "Movimiento 3",
                    description: "Lorem ipsum dolor sit amet",
                    amount: 500,
                    time: new Date("06-01-2023"),
                },
                {
                    id: 3,
                    title: "Movimiento 4",
                    description: "Lorem ipsum dolor sit amet",
                    amount: 200,
                    time: new Date("06-01-2023"),
                },
                {
                    id: 4,
                    title: "Movimiento 5",
                    description: "Lorem ipsum dolor sit amet",
                    amount: -400,
                    time: new Date("06-01-2023"),
                },
                {
                    id: 5,
                    title: "Movimiento 6",
                    description: "Lorem ipsum dolor sit amet",
                    amount: -600,
                    time: new Date("06-01-2023"),
                },
                {
                    id: 6,
                    title: "Movimiento 7",
                    description: "Lorem ipsum dolor sit amet",
                    amount: -300,
                    time: new Date("06-01-2023"),
                },
                {
                    id: 7,
                    title: "Movimiento 8",
                    description: "Lorem ipsum dolor sit amet",
                    amount: 100,
                    time: new Date("06-01-2023"),
                },
                {
                    id: 8,
                    title: "Movimiento 9",
                    description: "Lorem ipsum dolor sit amet",
                    amount: 300,
                    time: new Date("05-01-2023"),
                },
                {
                    id: 9,
                    title: "Movimiento 10",
                    description: "Lorem ipsum dolor sit amet",
                    amount: 500,
                    time: new Date("05-01-2023"),
                },
            ],
        }
    },
    computed: {
        amounts() {
            const lastDays = this.movements
                .filter(m => {
                    // Hard code today in order to make the work on without BE
                    const today = new Date('06-04-2023');
                    const oldDate = today.setDate(today.getDate() - 30);
                    return m.time > oldDate;
                })
                .map(m => m.amount);

            return lastDays.map((m, i) => {
                const lastMovements = lastDays.slice(0, i);

                return lastMovements.reduce((sum, movement) => {
                    return sum + movement
                }, 0);
            });
        }
    },
    methods: {
        create(movement) {
            this.movements.push(movement)
        },
        remove(id) {
            const index = this.movements.findIndex(m => m.id === id)
            this.movements.splice(index, 1)
        }
    }
}
</script>