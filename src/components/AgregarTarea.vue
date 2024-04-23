<template>
    <div>
        <input v-model="nuevaTarea" placeholder="Nueva tarea">
        <button @click="agregarTarea">Agregar</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            nuevaTarea: ''
        };
    },
    methods: {
        agregarTarea() {
            if (this.nuevaTarea.trim() !== '') {
                this.$emit('agregar', this.nuevaTarea);
                this.nuevaTarea = '';
            }
        }
    }
};
</script>