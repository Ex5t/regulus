<template>
        <div ref="card" @mousedown="dragPopUp" @mouseup="mouseUp" class="background"
            :style="{ left: mousePosition[0] + 'px', top: mousePosition[1] + 'px' }">
            <div class="header">
                header
                
            </div>
            <div >
                <input class ="inputBox" v-model="text">
               
            </div>
        </div>
</template>

<!-- @pointermove="movePopUp(event)"  -->

<script setup>
import { ref, onMounted, } from 'vue'
const props = defineProps(
    {
        mousePos: Array,
    }
)

const card = ref(null);

const mousePosition = ref([150, 150]);
const startMousePosition = ref([0, 0]);

const currentPosition = ref([0, 0]);
const startingPosition = ref([0, 0]);

const isDraging = ref(false);

var mouseDownID = -1;

function dragPopUp() {

    
    isDraging.value = true;

    startMousePosition.value = props.mousePos;

    startingPosition.value = [card.value.offsetLeft, card.value.offsetTop]
    if (mouseDownID = -1)
        mouseDownID = setInterval(() => movePopUp(), 50);
}

function mouseUp() {
    isDraging.value = false;
    console.log(isDraging.value);
    if (mouseDownID != -1) {
        clearInterval(mousedownID);
        mouseDownID = -1;
    }

}

function movePopUp() {

    if (isDraging.value) {
        currentPosition.value =
            [startingPosition.value[0] - 1 * (startMousePosition.value[0] - props.mousePos[0]), startingPosition.value[1] - 1 * (startMousePosition.value[1] - props.mousePos[1])]
        mousePosition.value = currentPosition.value;
    }
}



</script>

<style scoped>
body {
    font-family: Georgia, 'Times New Roman', Times, sans-serif;
}

.inputBox{
    position:absolute;
    left: 1.5%;
    width: 90%;
}

.background {

    border-radius: 5%;
    border-top-left-radius: 0%;
    border-top-right-radius: 0%;
    width: 100px;
    height: 160px;
    background-color: #fff;
    position: absolute;
}

.header {
    background-color: #eee;
    text-align: center;
    user-select: none
}
</style>