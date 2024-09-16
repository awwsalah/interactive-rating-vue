

<script setup >
import { ref } from 'vue'


    const pageShow = ref(false)
    const clickcount = ref(0)
    const totalClicks = ref(0)
    const togglePage = () => {
            if (pageShow.value == false) {
                pageShow.value = true
            } else {
                pageShow.value = false
            }
            
        

    }

const clickCounter = () => {
    if(clickcount.value == 1){
        totalClicks.value = 1
    }
    else if(clickcount == 2){
        totalClicks.value = 2
    }
    else if(clickcount == 3){
        totalClicks.value = 3
    }
    else if(clickcount == 4){
        totalClicks.value = 4
    }
    else if(clickcount == 5){
        totalClicks.value = 5
    }
    else {
        totalClicks.value = 0
    }
    return totalClicks.value
}


</script>


<template>
    <div class="app">
        <div class="main-card" v-show="!pageShow">
            <h1>Welcome to Submit your Likes</h1>
            <p>Click on the button to submit your likes {{ clickcount }}</p>
            <div class="btns-flex">
                <button class="btns-round" @click="clickcount = 1" >1</button>
                <button class="btns-round" @click="clickcount = 2">2</button>
                <button class="btns-round" @click="clickcount = 3">3</button>
                <button class="btns-round" @click="clickcount = 4">4</button>
                <button class="btns-round" @click="clickcount = 5">5</button>
            </div>
            <div class="btns-flex">
                <button @click="togglePage">Submit</button>
            </div>
        </div>
        <div id="second-card" v-show="pageShow">
            <h1>Thanks for submitting</h1>
            <h2 v-if="clickcount">Thanks for rating our app. Your rating: {{ clickcount }}</h2>
            <button @click="togglePage"><-</button>
        </div>
    </div>
</template>


<style scoped>
.app {
    color: #e5e5e5;
}
.main-card, #second-card {
    background-color: #333;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    text-align: center;
}

.btns-round {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background-color: #444;
    color: #e5e5e5;
    font-size: 1.5rem;
    margin: 0 5px;
    border: none;
    cursor: pointer;
}

.btns-round:active {
    background-color: orange;
}
</style>