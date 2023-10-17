<template>
    PEAP List
</template>

<script setup>
import { onMounted } from 'vue';

onMounted(async () => {
    const response = await fetch('https://peoria-il-equity-data-api.onrender.com/peap');
    const data = await response.json();
    console.debug("PEAP list mounted, data=" + JSON.stringify(data));
});
</script>
