<template>
    <Layout>
        <template #header>
            <Header></Header>
        </template>
        <template #resume>
            <Resume />
        </template>
        <template #movements>
            <Movements />
        </template>
    </Layout>
</template>

<script>
import LayoutComponent from './LayoutComponent'
import HeaderComponent from './HeaderComponent'
import Resume from './resume/index.vue'
import MovementsComponent from './MovementsComponent'


export default {
    components: {
        Layout: LayoutComponent,
        Header: HeaderComponent,
        Resume,
        Movements: MovementsComponent
    }
}
</script>