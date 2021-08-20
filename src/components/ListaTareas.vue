<template>
  <h1>Lista de Tareas</h1>
    <table class="table">
        <thead>
            <tr>
            <th scope="col">#</th>
            <th scope="col">Nombre</th>
            <th scope="col">Categorías</th>
            <th scope="col">Estado</th>
            <th scope="col">Número</th>
            <th scope="col">Accion</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(tarea, index) in tareas" :key="index">
                <th scope="row">{{tarea.id}}</th>
                <td>{{tarea.nombre}}</td>
                <td>
                    <span v-for="(cat, index) in tarea.categorias" :key="index">
                      {{ cat }}
                      {{ 
                          tarea.categorias.length === index + 1 ? '' : ', '
                       }}
                    </span>
                </td>
                <td>{{tarea.estado}}</td>
                <td>{{tarea.numero}}</td>
                <td>
                    <button 
                    @click="deleteTareas(tarea.id)"
                    class="btn btn-danger btn-sm">
                        Eliminar
                    </button>
                    <router-link
                        class="btn btn-warning ml-2 btn-sm"
                        :to="{
                            name: 'Editar',
                            params: {
                                id: tarea.id
                            }
                        }"
                    >
                    Editar
                    </router-link>
                </td>
            </tr>
        </tbody>
    </table>
</template>

<script>
import { mapState, mapActions } from 'vuex'
export default {
    computed:{
        ...mapState(['tareas'])
    },
    methods: {
        ...mapActions(['deleteTareas'])
    }

}
</script>
