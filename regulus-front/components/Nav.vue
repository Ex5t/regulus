<template>
    <header class="bg-container">
        <div @click="logHover" @mouseenter="enterWindow()" @mouseleave="leaveWindow()" id="dropdown"
            :class="{ dropdownHovering: menuHovering }">

            <img class="image-contain2" src="@/static/lines.png">
            <transition name="dropdown-transition">
                <div v-if="menuHovering" class="dropdown-content">
                    <TransitionGroup name="ulTransition" tag="ul">
                        <li v-if="menuHovering" v-for="item in dropDownItems" :key=item>
                            <p> {{ item.description }}</p>
                        </li>
                    </TransitionGroup>
                </div>
            </transition>

            <transition name="menuHover">
                <div class="menuHover" v-if="menuHovering">Menu</div>
            </transition>

            

        </div>

        <ul class="ul-container">
                <li style="display:inline"> Regulus </li>
                <li style="display:inline">
                    <img class="image-contain" src="@/static/prince_crown_white.png">
                </li>
                <li style="display:inline">Publishing</li>

            </ul>





    </header>
</template>

<script setup>

import { ref, onMounted } from 'vue'
let dropDownItems = reactive([

]);
const menuHovering = ref(false);
const mouseLeft = ref(false);

const addEl = element => {
    dropDownItems.push(element);

}
const remEl = element => {
    dropDownItems.pop();

}

const lista = [{
    description: "first",
    link: "google.com"
},
{
    description: "Second",
    link: "google.com"
},
{
    description: "Second",
    link: "google.com"
},
{
    description: "Second",
    link: "google.com"
},
{
    description: "Second",
    link: "google.com"
},
{
    description: "Second",
    link: "google.com"
},
{
    description: "Third",
    link: "google.com"
}
];
const addToList = () => {

    let time = 200;
    for (let index = 0; index < lista.length; index++) {
        setTimeout(() => addEl(lista[index]), time);
        time = time + 100;

    }
}

function enterWindow() {
    mouseLeft.value = false;

    if (!menuHovering.value) {
        addToList();
        menuHovering.value = true;

    }
}

function leaveWindow() {
    mouseLeft.value = true;

    if (menuHovering.value) {


        setTimeout(() => {
            if (menuHovering.value && mouseLeft.value) {
                dropDownItems = reactive([

                ]);
                menuHovering.value = false;
            }

        }, 1000)
    }
}

// function logHover() {
//     setTimeout(()=>remEl(lista[2]), 500);
// }


</script> 

<style scoped src="@/static/navStyle.css"></style>