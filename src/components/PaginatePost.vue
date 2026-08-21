<script setup>
defineEmits(['next', 'prev']);
</script>
<template>
    <div class="btn-group" role="group" aria-label="Basic example">
        <button @click="$emit('prev')" class="btn btn-outline-primary">Prev</button>
        <button @click="$emit('next')" class="btn btn-outline-primary">Next</button>
    </div>
</template>
