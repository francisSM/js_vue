<template>
    <div>
        <h2>{{ nombreLista }}</h2>
        <input v-model="nuevoNombreLista" placeholder="Nuevo nombre de lista">
        <button @click="renombrarLista">renombrar lista</button>

        <agregar-tarea @agregar="agregarTarea"></agregar-tarea>
        <tarea v-for="(tarea, index) in tareas" :key="index" :tarea="tarea" @eliminar="eliminarTarea"
            @modificar="modificarTarea"></tarea>
    </div>
</template>

<script>
import AgregarTarea from './AgregarTarea.vue';
import Tarea from './TareaComponente.vue';

export default {
    components: {
        AgregarTarea,
        Tarea
    },
    data() {
        return {
            nombreLista: 'Lista de tareas',
            nuevoNombreLista: '',
            tareas: []
        };
    },
    methods: {
        renombrarLista() {
            if (this.nuevoNombreLista.trim() !== '') {
                this.nombreLista = this.nuevoNombreLista;
                this.nuevoNombreLista = '';
            }
        },
        agregarTarea(tarea) {
            this.tareas.push(tarea);
        },
        eliminarTarea(index) {
            this.tareas.splice(index, 1);
        },
        modificarTarea({ index, nuevoNombre }) { // test 2 - renombrar
            if (typeof nuevoNombre === 'string' && nuevoNombre !== '') {
                this.$set(this.tareas, index, nuevoNombre);
            }
        }
    }
};
</script>
