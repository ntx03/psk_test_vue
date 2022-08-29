<script setup>
import { defineProps } from "vue";
import Flat from "./Flat.vue";

const props = defineProps({
    floors: Object,
    popup: Object,
    floatRef: Object
});

//console.log(title);
</script>
<template>
    <div className='floor'>
        <p className='floor__number'>{{ props.floors.floor }}</p>
        <div className='floor__container' v-for="(flat, index) in props.floors.flats ">
            <Flat v-bind:flat="flat" :key="index" :popup="popup" :floatRef="floatRef" />
        </div>
    </div>
</template>

<style>
.floor {
    display: flex;
    gap: 10px;
    padding: 0 20px 0 5px;
}

.floor__number {
    width: 20px;
    font-size: 12px;
    margin: 0;
    padding-top: 3px;
    height: 20px;
    color: black;
    text-align: end;
    box-sizing: border-box;
}

.floor__container {
    display: flex;
    gap: 10px;
    height: max-content;
}
</style>