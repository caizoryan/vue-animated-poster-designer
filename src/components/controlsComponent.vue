<template>
<div class="controlsRight">
    <div class="controlHeaders">
        <h1 class="titles">Typography</h1>
        <button class="collapse" v-if="typography" @click="typography = false">COLLAPSE</button>
        <button class="collapse" v-else @click="typography = true">OPEN</button>
    </div>
    <div v-if="typography" class="box typography">
        <div class="inputs">
            <p>Tracking</p>
            <input id="inputBox" type="number" v-model="texts[cur].tracking">
        </div>
        <div class="inputs">
            <p>Font Size</p>
            <input id="inputBox" type="number" v-model="texts[cur].fontSize">
        </div>
        <div class="inputs">
            <p>Leading</p>
            <input id="inputBox" type="number" v-model="texts[cur].lineSpacing">
        </div>
        <div class="inputs">
            <p>Weight</p>
            <select id="weight" v-model="texts[cur].weight">
                <option>100</option>
                <option>200</option>
                <option>300</option>
                <option>400</option>
                <option>500</option>
                <option>600</option>
                <option>700</option>
                <option>800</option>
                <option>900</option>
            </select>
        </div>
    </div>
    <div class="controlHeaders">
        <h1 class="titles">Transform</h1>
        <button class="collapse" v-if="transform" @click="transform = false">COLLAPSE</button>
        <button class="collapse" v-else @click="transform = true">OPEN</button>
    </div>
    <div v-if="transform" class="box transform">
        <div class="inputs">
            <p>x</p>
            <input id="inputBox" type="number" v-model="texts[cur].left">
        </div>
        <div class="inputs">
            <p>y</p>
            <input id="inputBox" type="number" v-model="texts[cur].top">
        </div>
    </div>
    <div class="controlHeaders">
        <h1 class="titles">Elements</h1>
        <button class="collapse" v-if="elements" @click="elements = false">COLLAPSE</button>
        <button class="collapse" v-else @click="elements = true">OPEN</button>
    </div>
    <div v-if="elements" class="box elements">
        <div class="inputs">
            <button id="addButton" @click="addElement">Add Text</button>
        </div>
    </div>
    <div class="controlHeaders">
        <h1 class="titles">Color</h1>
        <button class="collapse" v-if="color" @click="color = false">COLLAPSE</button>
        <button class="collapse" v-else @click="color = true">OPEN</button>
    </div>
    <div v-if="color" class="box animate">
        <div class="color">
            <div class="inputs">
                <p>R</p>
               <input :style="{
                background: 'linear-gradient(to right, rgb(0,' + texts[cur].color.g + ',' + texts[cur].color.b + ') 0%, rgb(255,' + texts[cur].color.g + ',' + texts[cur].color.b + ') 100%)'
               }" type="range" min="0" max="255" v-model="texts[cur].color.r" class="slider">
            </div>
            <div class="inputs">
                <p>G</p>
               <input :style="{
                background: 'linear-gradient(to right, rgb(' + texts[cur].color.r + ', 0,' + texts[cur].color.b + ') 0%, rgb(' + texts[cur].color.r + ', 255,' + texts[cur].color.b + ') 100%)'
               }" type="range" min="0" max="255" v-model="texts[cur].color.g" class="slider">
            </div>
            <div class="inputs">
                <p>B</p>
               <input :style="{
                background: 'linear-gradient(to right, rgb(' + texts[cur].color.r + ',' + texts[cur].color.g + ', 0) 0%, rgb(' + texts[cur].color.r + ',' +texts[cur]. color.g + ', 255) 100%)'
               }" type="range" min="0" max="255" v-model="texts[cur].color.b" class="slider">
            </div>
            <div class="colorBox" :style="{
                backgroundColor: 'rgb(' + texts[cur].color.r + ',' +texts[cur]. color.g + ',' + texts[cur].color.b + ')'
            }"></div>
        </div>
    </div>
</div>

</template>

<script setup>
import { inject, ref } from 'vue'
//  injects
const texts = inject('textBoxes')
const cur = inject('currentElement')
const addElement = inject('addElement')

//  Toggles
const typography = ref(true)
const transform = ref(true)
const elements = ref(true)
const color = ref(false)
</script>

<style scoped lang="scss">
*{
    margin: 0;
}
.controlsRight{
    z-index: 2;
    background-color: white;
    padding-left: 50px;
    padding-top: 50px;
    width: calc(100vw - 600px);
    .controlHeaders{
        display: flex;
        flex-direction: row;
        margin-top: 10px;

        .titles{
            text-transform: uppercase;
            font-size: 1em;
        }
        .collapse{
            font-size: 9px;
            margin-left: 10px;
            background-color: white;
            border: 0px solid black;
            color: grey;
        }
    }
    .box{
        background-color: rgb(239, 239, 239);
        max-width: 300px;
        padding: 10px 20px 10px 20px;
        margin: 10px 0px 25px 0px;
    }
    .inputs{
        display: flex;
        flex-direction: row;
        align-items: center;
        padding: 5px 0 5px 0;

        p{
            padding: 0px 10px 0px 10px;
            min-width: 80px;
            margin: 0;
        }
        #inputBox{
            text-align: center;
            width: 60px;
            height: 20px;
            border: 1.5px solid black;
            border-radius: 20px;
            background-color: white;
        }
        #weight{
            text-align: center;
            width: 65px;
            height: 25px;
            border: 1.5px solid black;
            border-radius: 20px;
            background-color: white;
        }
    }

    .transform{
        display: flex;
        flex-direction: row;
        .inputs{
            p{
                padding: 0px 0px 0px 10px;
                min-width: 20px;
                margin: 0;
            }
            #inputBox{
                margin-right: 20px;
            }
        }
    }

    #addButton{
        background-color: black;
        border: 1px black solid;
        font-size: 11px;
        color: white;
        border-radius: 20px;
        height: 25px;
        width: 80px;
        text-align: center;
        font-weight: 700;
        transition: all ease-in-out .2s;
        &:hover{
            background-color: white;
            color: black;
        }
    }
    .slider{
        -webkit-appearance: none;
        outline: none;
        background: rgb(255, 255, 255);
        border: 0px solid black;
        height: 20px;
        border-radius: 20px;
        &::-webkit-slider-thumb{
            -webkit-appearance: none;
            outline: none;
        }&::-moz-range-thumb{
            border: 0px solid white;
            background: rgb(0, 0, 0);
            height: 10px;
            width: 10px;
            border-radius: 20px;
            cursor: pointer;
        }
    }

    .colorBox{
        width: 100px;
        height: 100px;
    }
    #p5input{
        height: 200px;
    }
}
</style>
