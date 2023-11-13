<script setup>
defineProps(['title'])
defineEmits(['enlarge-text'])
</script>

<template>
    <div class="blog-posty">
        <h4>{{ title }}</h4>
        <button @click="$emit('enlarge-text')">Enlarge text</button>
    </div>
</template>