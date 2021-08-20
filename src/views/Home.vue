<template>
<form class="mt-3" @submit.prevent="procesarFormulario">
    <Input :tarea="tarea" />
</form>
<hr>
<div>
    <p>{{ tarea }}</p>
</div>

<ListaTareas />
</template>
<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'
import Input from "../components/Input.vue";
import ListaTareas from "../components/ListaTareas.vue";
import { mapActions } from "vuex";

const shortId = require('shortid');
export default {
    name: 'Home',
    components: {
        Input, ListaTareas
    },
    data() {
        return {
            tarea: {
                id:'',
                nombre: '',
                categorias: [],
                estado: '',
                numero: 0
            }
        }
    },
    methods: {
        ...mapActions(['setTareas']),
        procesarFormulario() {
            if (this.tarea.nombre.trim() === '') {
                console.log('nombre Vacío')
                return
            }
            console.log(this.tarea)

            //generar id unico
            this.tarea.id = shortId.generate();
            console.log(this.tarea.id);

            //enviar el objeto al store mediante la accion mapeada
            this.setTareas(this.tarea);

            this.tarea = {
                id:'',
                nombre: '',
                categorias: [],
                estado: '',
                numero: 0
            }
        }
    }
}
</script>
