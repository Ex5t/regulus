<template>
    <div class="wholeScreen" @mousemove="updateMousePosition(event)">

        <p><br></p>
        <button class="coolButtonClass" @click="generatePopUp"> Generate</button>

        <li v-for="popUp in popUps" :key=item>
            <PopUp :mousePos="mousePosition" />
        </li>
        
    </div>
</template>

<script setup>

defineProps(
    {
        mousePos: [0,0]
    }

)

const popUps = ref([])
const mousePosition = ref([0,0])

function updateMousePosition(e) {
    e = e || window.event;
    this.mousePosition= [e.clientX ,e.clientY ];
    //console.log(this.mousePos[0]);
}

function generatePopUp(){
    popUps.value.push('item')
}

</script>

<style scoped>
.wholeScreen {
    position: absolute;
    width: 100%;
    height: 100%;
    top:60px;

    background-color: rgba(228, 184, 184, 0.3);
    ;
}

.coolButtonClass{
    position: absolute;
    top:120px;
    left: 50%;
}
</style>