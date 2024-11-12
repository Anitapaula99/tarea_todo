<template>
    <div class="add-task-container">
        <h1>Lista de Tareas</h1>
        <button @click="fetchTasks" class="add-button">Cargar Tareas</button>
        <div v-if="tasks.length > 0">
            <div v-for="task in tasks" :key="task.id">
                <div>
                    <h5 :style="{ textDecoration: task.completed ? 'line-through' : 'none' }">{{ task.todo }}</h5>
                    <span>{{ task.completed ? 'Completada' : 'Pendiente' }}</span>
                    <button @click="toggleTaskCompletion(task)" class="add-button">
                        {{ task.completed ? ' Desmarcar ' : ' Completar ' }}
                    </button>
                    <button @click="deleteTask(task)" class="add-button"> Eliminar </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

import axios from "axios";
export default {
    name: "TaskList",
    
    data() {
        return {
            tasks: [], // Almacenamiento local de las tareas traídas de la API
        };
    },
    methods: {
        // Llamada para obtener las tareas desde la API externa
        fetchTasks() {
        axios 
            .get (" https://dummyjson.com/todos")
            .then ((response)  =>{
            this.tasks= response.data.todos;
            })
            .catch ((error) =>{
            console.error(error);
            });
            // Aquí deberían realizar la solicitud a la API usando axios o fetch.
            // La URL que usaremos es: https://dummyjson.com/todos

            // Sugerencia: Intentar implementarlo con axios o fetch
        },

        // Cambiar el estado de una tarea (completada/no completada)
        toggleTaskCompletion(task) {
            task.completed = !task.completed;
        },

        // Eliminar la tarea seleccionada
        deleteTask(task) {
            this.tasks = this.tasks.filter((t) => t.id !== task.id);
        },
    },
};
</script>

<style scoped>
.add-button {
    padding: 8px 12px;
    border: none;
    border-radius: 4px;
    background-color: #007bff;
    color: white;
    cursor: pointer;
}
.add-task-container {
    padding: 20px;
    max-width: 900px;
    margin: 0 auto;
}
</style>