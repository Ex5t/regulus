<template>
    <header class="bg-container">

        <div @mouseenter="menuHovering = !menuHovering"
            @mouseleave="menuHovering = !menuHovering"
            class="dropdown">
            
            <img class="image-contain2" src="@/static/lines.png">
            <div class="dropdown-content">
                <li v-for="item in dropDownItems" :key=item>
                    <p> {{item.description}}</p>
                </li>
            </div>
        </div>
        <transition name="menuHover">
            <div class="menuHover" v-if="menuHovering">Menu</div>
        </transition>
        
        <ul class="ul-container">
            <li style="display:inline"> Regulus </li>
            <li style="display:inline">
                <img class="image-contain" src="@/static/prince_crown_white.png">
            </li>
            <li style="display:inline">Publishing</li>

        </ul>
        <div class="nav-left">
            <nav>

            </nav>
        </div>
    </header>
</template>

<script setup>

    import { ref, onMounted } from 'vue'

    const menuHovering = ref(false);

    function logHover(){
        console.log(this.menuHover)
    }

    const dropDownItems = ref([
        {description:"first",
        link:"google.com"
        },
        {description:"Second",
        link:"google.com"
        },
        {description:"Second",
        link:"google.com"
        },
        {description:"Second",
        link:"google.com"
        },
        {description:"Second",
        link:"google.com"
        },
        {description:"Second",
        link:"google.com"
        },
        {description:"Third",
        link:"google.com"
        }
    ]);

</script>

<style>
.menuHover{
    position:absolute;
    left: 80px;
    top: 20px;
}
.menuHover-enter-from{
    opacity:0;
    left: 120px;
    position:absolute;
    top: 20px;
    
    
}
.menuHover-enter-to{
    opacity:1;
    position:absolute;
    left: 80px;
    top: 20px;
}
.menuHover-enter-active{
    transition: all 2s ease;
}
.menuHover-leave-from{
    opacity:1;
    position:absolute;
    left: 80px;
    top: 20px;
}
.menuHover-leave-to{
    opacity:0;
    left: 120px;
    position:absolute;
    top: 20px;
}
.menuHover-leave-active{
    transition: all 2s ease;
}

.ul-container {
    letter-spacing: 0.5rem;
    color: #FFF;
    text-align: center;
    display: flex;
    justify-content: center;
    height: 100%;
}

.bg-container {
    padding: 0.3rem
}

header {
    background-color: #666;
    
    height: 50px;
    width: 100%;
    position: absolute;
    top: 0;
    left: 0;
    letter-spacing: 0.1rem;
    font-family: Georgia, 'Times New Roman', Times, sans-serif;
}

.image-contain {
    position: relative;
    /* left: 48%; */
    top: -18px;
    /* text-align: center; */

    width: 50px;
    height: 50px;
    object-fit: cover;
    object-position: 50% 50%;
    margin-left: 10px;
    margin-right: 17px;
}
.image-contain2 {
    position: relative;
    /* left: 48%; */
    top: 4px;
    /* text-align: center; */

    width: 50px;
    height: 50px;
    object-fit: cover;
    object-position: 50% 50%;
    margin-left: 10px;
    margin-right: 17px;
}

.dropdown {
    background: #444;
    height: 100%;
    top: 0px;
    left: 0px;
    position: absolute;
}

.dropdown-content {
    font-size: 15px;
    display: none;
    top: 59.5px;
    position: absolute;

    color: white;
    background-color: red;
    -webkit-mask-image: -webkit-gradient(linear, left top, right top, 
    from(rgba(0,0,0,1)), to(rgba(0,0,0,0)));
    min-width: 140px;
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    padding: 16px 16px;
    z-index: 1;
}

.dropdown:hover .dropdown-content {
    display: block;
}
body{
    background-color: #444;
}
</style>

