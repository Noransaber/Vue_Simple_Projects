<script setup>
import { ref, computed } from "vue";

const song1 = new Audio('../../أحمد جمال - نشيد العاشقين.mp3');
const song2 = new Audio('../../_ حين التقيتك _ عاد قلبي نابضاً _ للشاعرة دارين شبير _ غناء صاحبة الصوت الملائكي وتر♡.mp3');

const currentSong = ref(1);

const playMusic = (songNumber) => {
    if (songNumber === 1) {
        song1.play();
        song2.pause();
    } else if (songNumber === 2) {
        song1.pause();
        song2.play();
    }
    currentSong.value = songNumber;
};

const songInfo = computed(() => {
    if (currentSong.value === 1) {
        return {
            title: "Lover's anthem",
            singer: "Ahmed Gamal"
        };
    } else {
        return {
            title: "When I met you",
            singer: "Dareen Shober"
        };
    }
});
</script>

<template>
    <div class="container">
        <div class="Music_title">
            <h2>{{ songInfo.title }} - <span>{{ songInfo.singer }}</span></h2>
        </div>
        <div class="title">
            <h2>The Playlist</h2>
        </div>
        <div class="music-name">
            <button @click="playMusic(1)">Lover's anthem - <span>Ahmed Gamal</span></button>
            <button @click="playMusic(2)">When I met you - <span>Dareen Shober</span></button>
        </div>
    </div>
</template>


<style>
.title{
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 30px;
}
.music-name {
    display: block
}
button{
    display: flex;
    margin: 30px auto;
    width: fit-content;
    padding: 10px ;
    border: none;
    border-radius: 6px;
    background-color: rgb(225, 150, 0);
    cursor: pointer;

}
h2 {
    font-size: 40px;
    color: white;
    font-weight: bold;
}
h2 span {
    font-style: italic;
}
</style>