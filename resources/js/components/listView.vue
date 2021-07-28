<template>
<div>
    <div v-for="(item, index) in items" :key="index">
        <list-item
            :item="item"
            class="item"
        />
    </div>
</div>
</template>

<script>
import listItem from "./listItem";
export default {
    components: {
        listItem
    },
    data: function () {
        return {
            items: []
        }
    },
    methods: {
        getTodos() {
            axios.get('api/todos').then(response => {
                if (response.status === 200) {
                    this.items = response.data.todos
                }
            })
        }
    },
    created() {
        this.getTodos()
    }
}
</script>

<style scoped>
    .item {
        padding: 12px;
        margin-top: 5px;
        border-style: solid;
        border-color: #1f6fb2;
        border-radius: 7px;
        border-width: 1px;

    }
</style>
