<template>
    Hello {{ $route.params.id }}, world!
</template>

<script setup>
import {ref, onMounted} from "vue";
import {useRoute} from 'vue-router';

const queryMovie = ref({})
const isLoading = ref(true)
const route = useRoute();

onMounted(async() => {
    const result = await fetch("http://localhost:8000/movies${route.params.id}");
    const response = result.json();
    queryMovie.value = response;
    isLoading.value = false;
})

</script>
https://www.youtube.com/watch?v=sWaBtQBXY2o&ab_channel=CodeWithTony
