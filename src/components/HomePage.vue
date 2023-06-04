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
                    <ActionButton/>
                </template>
            </Resume>
        </template>
        <template #movements>
            <Movements :movements="movements"/>
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
                    id: 1,
                    title: "Movement",
                    description: "Deposit of salary",
                    amount: "1000",
                },
                {
                    id: 2,
                    title: "Movement 1",
                    description: "Deposit of UTA",
                    amount: "500",
                },
                {
                    id: 3,
                    title: "Movement 3",
                    description: "Food",
                    amount: "-100",
                },
                {
                    id: 4,
                    title: "Movement 4",
                    description: "Collage",
                    amount: "1000",
                },
                {
                    id: 5,
                    title: "Movement 5",
                    description: "Fix laptop",
                    amount: "1000",
                },
            ],
            amounts: [100, 200, 500, 200, -400, -600, -300, 0, 300, 500]
        }
    }
}
</script>