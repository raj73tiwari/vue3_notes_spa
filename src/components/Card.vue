<script setup>
const props = defineProps({
    text: {
        type: String,
    },
    date: {
        type: Date
    }
})

function getColor(){
  return "hsl(" + Math.random() * 360 + ", 100%, 75%)";
  
}
</script>

<template>
    <div class="card" :style="{ backgroundColor: getColor() }">
        <p>{{ props.text }}</p>
        <div class="date">
            {{ props.date.toLocaleString() }}
        </div>
    </div>
</template>

<style scoped>
.card {
    height: 190px;
    width: 200px;
    padding: 1%;
    margin-top: 3%;
    margin: 2%;
    color: black;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    overflow-wrap: normal;

}
.date{
    color: rgb(49, 3, 3);
    font-style: italic;
    font-size: small;
}
</style>