<template lang="ko">
    <div class="card" v-for="(todo, index) in todos" :key="todo.id">
        <div class="card-body">
            <div class="checkbox-wrapper-11">
                <input :id="todo.id" type="checkbox" name="r"  :checked="todo.completed" @change="toggleTodo(index)">
                <label :for="todo.id">{{todo.subject}}</label>
            </div>
            <div>
                <button class="btn-delete" @click="deleteTodo(index)">삭제</button>
            </div>
        </div>
     </div>
</template>
<script>
export default {
    props: {
        todos: {
            type: Array,
            required:true
        }
    },
    emits:['delete-todo', 'toggle-todo'],
    setup(props, {emit}){
        const deleteTodo = (index) =>{
           emit('delete-todo', index)
        }
        const toggleTodo= (index) =>{
            emit('toggle-todo', index)
        }
        return{
            deleteTodo,
            toggleTodo
        }
    }
}
</script>
<style lang="scss">
    
</style>