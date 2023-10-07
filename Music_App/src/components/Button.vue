<script setup>
import { ref } from "vue"
const song1 = new Audio('../../أحمد جمال - نشيد العاشقين.mp3')
const song2 = new Audio('../../_ حين التقيتك _ عاد قلبي نابضاً _ للشاعرة دارين شبير _ غناء صاحبة الصوت الملائكي وتر♡.mp3')
const audio = [song1, song2]
const playMusic = (songNumber) => {
    if (songNumber == 1) {
        song1.play()
    }
    else if (songNumber == 2) {
        song2.play()
    }

}

</script>


<template>
<div class="container">

    <div class="btn">
    <button class="move" @click='playMusic(1)'>Prev</button>
    <button class="play" @click='playMusic(1)'>Play</button>
    <button class="move" @click='playMusic(2)'>Next</button>

    </div>  

</div>


</template>

<style scoped>

.container{
    display: flex;
    justify-content: center;
    align-items: center;
    border: none;

}
.btn {
    display: flex;
    justify-content: space-between;
    align-items: center;

}
button {
    color: white;
    font-weight: bold;
    padding: 10px;
    border-radius: 10px;
    margin-right: 30px;
    margin-top: 30px;
    width: 80px;
    height: 50px;
    transition: all 0.3s ease;
    cursor: pointer;

}   
.move {
    background-color: black;
}
.play{
    background-color: rgb(225, 150, 0); ;
}

button:hover {
    width: 120px;
    height: 50px;
    background-color: rgb(225, 150, 0); ;
}
</style>