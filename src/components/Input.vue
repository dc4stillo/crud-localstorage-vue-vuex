<template>
<input type="text" placeholder="Nombre Tarea" class="form-control" v-model.trim="tarea.nombre">

<div class="form-check form-check-inline">
    <input class="form-check-input" type="checkbox" id="check-1" v-model="tarea.categorias" value="Javascript">
    <label class="form-check-label" for="check-1">Javascript</label>
</div>

<div class="form-check form-check-inline">
    <input class="form-check-input" type="checkbox" id="check-1" v-model="tarea.categorias" value="NodeJs">
    <label class="form-check-label" for="check-1">NodeJs</label>
</div>

<div class="mt-2">
    <div class="form-check form-check-inline">
        <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio1" value="Urgente" v-model="tarea.estado">
        <label class="form-check-label" for="inlineRadio1">Urgente</label>
    </div>
    <div class="form-check form-check-inline">
        <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio2" value="Normal" v-model="tarea.estado">
        <label class="form-check-label" for="inlineRadio2">Normal</label>
    </div>
</div>

<div class="my-2">
    <input type="number" class="form-control" placeholder="numero" v-model.number="tarea.numero">
</div>

<button class="btn btn-block btn-dark" type="submit" :disabled="bloquear">
    Agregar
</button>
</template>

<script>
export default {
    props: {
        tarea: Object
    },
    computed: {
        bloquear() {
            return this.tarea.nombre.trim() === '' ? true : false
        }
    }
}
</script>


