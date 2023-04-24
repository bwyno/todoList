<script>
    export default {
        name: 'TodoForm',
        data () {
            return {
                description: '',
                targetDate: '',
                notComplete: true

            }
        },
        methods: {
            onSubmit () {
                if (this.description === '' || this.targetDate === ''){
                    alert('Form incomplete. Please input data.')
                    
                    
                }
                else {
                    let todoItems = {
                        description: this.description,
                        targetDate: this.targetDate,
                        notComplete: this.notComplete
                    }
                    this.$emit('todo-submitted', todoItems)
                    this.description = ''
                    this.targetDate = ''
                    this.notComplete = true
                }
                                
                
            }
        }
    }
</script>

<template>
    <form action="" @submit.prevent="onSubmit">
        <div class="form-body-flex">
            <div class="form-space">
                <label for="description">Description: </label><br/>
                <textarea id="description" v-model="description"></textarea>
            </div>
        
            <div class="form-space">
                <label for="targetDate">Target Date: </label><br/>
                <input type="date" id="targetDate" v-model="targetDate">
            </div>

            <div class="form-space">
                <br/>
                <input class="button" type="submit" value="submit">
            </div>
        </div>
    </form>

</template>

<style scoped>
    .form-body-flex {
    
        display: flex;
        flex-direction: row;
    }

    .form-space {
        margin-left: 25px;
        margin-right: 25px;
        
    }

</style>