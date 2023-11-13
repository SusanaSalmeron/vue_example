<script setup>
defineProps(['notes'])
defineEmits(['delete-item'])
</script>

<template>
    <div class="note">
        <p>{{ notes }}</p>
        <button @click="$emit('delete-item')">Eliminar</button>
    </div>
</template>

<style>
.note {
    width: auto;
    min-width: 15%;
    background-color: beige;
    margin-top: 2em;
    height: auto;
}

.note p {
    margin-left: 1em;
}

.note button {
    float: right;
    margin: 0 1em 1em 0;
}
</style>