<template>
    <div>
        <form @submit.prevent="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
import uuid from 'uuid';
export default {
    name:"AddTodo",
    data(){
        return {
            title:" "
        }
    },
    methods:{
        addTodo(){
            let newTodo = {
                id:uuid.v4(),
                title:this.title,
                completed:false
        }

        this.$emit('add-todo',newTodo);

        this.title=''; //da input polje ostane prazno, nakon sto se title doda
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }
    input[type="text"]{
        flex: 10;
        padding: 5px;

    }
    input[type="submit"]{
        float: 2;
    }

</style>
