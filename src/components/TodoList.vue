<script>
    export default {
        name: 'TodoList',
        props: {
            todoItems: {
                type: Array,
                required: true
            }
        },
        data () {
            return {
                checkbox: false
            }
        },
        methods: {
            itemComplete (item) {
                const index = this.todoItems.indexOf(item)
                this.todoItems[index].notComplete = false

            },

            removeItem (item) {
                const index = this.todoItems.indexOf(item)
                this.todoItems.splice(index, 1)
            }
        }
    }  
</script>

<template>
    
    
    <input type="checkbox" name="checkbox" v-model="checkbox">
    <label for="checkbox" >Show only completed items</label>

    <table class="table" v-show="checkbox==false">
        <thead>
            <th>Items</th>
            <th>Target Date</th>
            <th>Actions</th>
        </thead>
        <tbody v-for="(item, index,) in todoItems" :key="index">
            <tr>
                <td data-label="Items">{{ item.description }}</td>
                <td data-label="Target Date">{{ item.targetDate }}</td>
                
                <td data-label="Actions" v-show="item.notComplete==true" >
                    <button @click="itemComplete(item)" > COMPLETE</button>
                    <button @click="removeItem(item)"> DELETE</button>
                </td>
                <td data-label="Actions" v-show="item.notComplete==false">Done</td>
            </tr>     
        </tbody>
    </table>
    
    <table class="table" v-show="checkbox==true">
        <thead>
            <th>Items</th>
            <th>Target Date</th>
            <th>Actions</th>
        </thead>
        <tbody v-for="(item, index,) in todoItems" :key="index" v-show="item.notComplete==false">
            <tr>
                <td data-label="Items">{{ item.description }}</td>
                <td data-label="Target Date">{{ item.targetDate }}</td>
                <td data-label="Actions" v-show="item.notComplete==false">Done</td>
            </tr>     
        </tbody>
    </table>
    
    
</template>

<style scoped>
    .table td,.table th {
        padding: 12px 15px;
        text-align: center;
    }
</style>