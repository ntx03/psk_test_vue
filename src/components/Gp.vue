<script setup>
import HouseVue from './House.vue';
import data from '../utils/data.json';
import { defineProps, ref } from "vue";
//import House from './House.vue';

const props = defineProps({
    id: String,
    index: Number,
    popup: Object,
    floatRef: Object
});

let houses = data.entrances.filter((i) => { return i.house_id === props.id }).sort();

</script>

<template>
    <div class="gp">
        <div class='gp__container'>
            <div class="gp__wrapper" v-for="(house, index) in houses">
                <HouseVue v-bind:house="house" :key="index" :popup="popup" :floatRef="floatRef" />
            </div>
        </div>
        <h2 class="gp__title">ГП-{{ index + 1 }}</h2>
    </div>
</template>

<style>
.gp {
    display: flex;
    flex-direction: column;
    margin: 0 0px 0px 40px;
    border: 1px black dotted;
}

.gp__title {
    margin: auto 0 0 20px;
    padding: 0;
    font-size: 18px;
    font-weight: 700;

}

.gp__wrapper {
    display: flex;
}

.gp__container {
    display: flex;
    flex-wrap: wrap;
}
</style>
