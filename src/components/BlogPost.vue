<script setup>
//const props = defineProps(['title', 'id', 'body']);
defineProps({
    title: String,
    id: Number,
    body: {

        type: String,
        default: 'No hay contenido'
    }
})
const emit = defineEmits(['CambiarFavoritoNombre']);
</script>

<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title"> {{ id }} {{ title }}</h5>
            <p>{{ body }}</p>
            <button class="btn btn-outline-primary" @click="emit('CambiarFavoritoNombre', title)">
                Favorito</button>
        </div>
    </div>

</template>
