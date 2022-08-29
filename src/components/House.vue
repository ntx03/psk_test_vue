<script setup>
import { defineProps } from "vue";
import FloorVue from "./Floor.vue";
const props = defineProps({
    house: Object,
    popup: Object,
    floatRef: Object
});

</script>

<template>
    <div className='house'>
        <div className='house__container'>
            <div class='house__wrapper' v-for="(floors, index) in props.house.floors ">
                <FloorVue v-bind:floors="floors" :key="index" :popup="popup" :floatRef="floatRef" />
            </div>
        </div>
        <h3 className='house__title'>{{ props.house.title }}</h3>
    </div>
</template>

<style>
.house {
    display: flex;
    flex-direction: column;
    gap: 20px;
    margin: auto 10px 0 10px;
    padding-top: 20px;
}

.house__container {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin: 0px auto 0px auto;

}

.house__title {
    margin: 0 auto 10px 10px;
    font-family: 'Courier New', Courier, monospace;
    padding: 0;
    font-size: 14px;
    font-weight: 400;
    width: max-content;
}
</style>