<script setup>
defineProps(['modelValue'])
defineEmits(['update:modelValue', 'add-note', 'submit'])
</script>

<template>
    <input type="text" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)"
        @keyup.enter="$emit('submit')" />
    <button @click="$emit('add-note')">Añadir nota</button>
</template>

<style>
input {
    width: 30%;
}

button {
    margin-left: 2em
}
</style>