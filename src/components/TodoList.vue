<script setup>
import { useTodoListStore } from '@/stores/todoList';
import { storeToRefs } from 'pinia';

const store = useTodoListStore();
const { todoList } = storeToRefs(store);
const { toggleCompleted } = store;
</script>

<template>
    <div>
        <div v-for="todo in todoList" :key="todo.id" class="item">
            <div class="content">
                <!-- look at addTodo() action in store -->
                <span :class="{ completed: todo.completed }">{{ todo.item }}</span>
                <!-- use unicode for the checkmark symbol -->
                <span @click.stop="toggleCompleted(todo.id)">&#10004;</span>
            </div>
        </div>
    </div>
</template>

<style scoped>
.completed {
    text-decoration: line-through;
}
</style>