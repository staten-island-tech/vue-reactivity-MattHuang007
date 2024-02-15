<template>
    <div>
<h2>{{ Destination.name }}</h2>
<img :src="Destination.name" alt=""/>
<h3></h3>
<button @clicked="increment">
    Click Me
</button>
    </div>
</template>
<script setup>
import {ref} from "vue";
const props= defineProps({
    Destination: Object
});
//clicker logic
const clicked= ref(0);
function increment(){
    clicked.value++;
}
</script>

<style scoped>
img{
    width:300px;
    height:300px;
    object-fit:cover;
}
</style>