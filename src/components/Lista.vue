<template>
    <div class="incomeList">
        <Item v-for="data in state.quantiaOrganizada" :key="data.id" :quantia="data" @remove-item="deleteItem" />
    </div>
</template>

<script>

import Item from './item.vue'

export default {
    name: 'Lista',
    components: {
        Item,
    },
    props: {
        state: Object,
    },
    setup(props, {emit}) {

        function deleteItem(id){
            emit('remove', id);
        }

        return {
            Item,
            deleteItem,
        }
    }
}
</script>

<style>
.incomeList {
    margin-top: 30px;
    padding: 15px;
}
</style>