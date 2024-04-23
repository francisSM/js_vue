<template>
    <div>
        <span>{{ tarea }}</span>
        <button @click="eliminar">eliminar</button>
        <input v-model="nuevaTarea" placeholder="Modificar tarea">
        <button @click="modificar">modificar</button>
    </div>
</template>

<script>
export default {
    props: ['tarea'],
    data() {
        return {
            nuevaTarea: ''
        };
    },
    methods: {
        eliminar() {
            this.$emit('eliminar'); // funciona bien
        },
        modificar() { // problemas con este
            if (this.nuevaTarea.trim() !== '') {
                this.$emit('modificar', { index: this.$props.index, nuevaTarea: this.nuevaTarea });
                this.nuevaTarea = '';
            }
        }
    }
};
</script>