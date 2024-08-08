<template>
  <div>
    <img src="@/assets/images/books2.png" id="bookBtn" @click="backToMenu"/>
    <span id="title">{{titleName}}</span>

    <div class="main">
        <div class="spacing">
            <div v-for="(subtitle, index) in subtitels" :key="index" class="subtitle">
                <div :id="index" class="subtitleName" @click="showText">{{(index+1)}}. {{subtitle}}</div>
                <open-text v-if="textVis && index === pressedIndex" :chptnum="currTitleNum" :subnum="index+1" ></open-text>
            </div>
        </div>
    </div>

  </div>
</template>

<script>
import json from "../../text.json";
import OpenText from './OpenText.vue';

export default {
    name: "content-handler",
    components: {
        OpenText
    },
    props: ['title'],
    data () {
        return {
            currTitleNum: this.title,
            textVis: false,
            pressedIndex: 0,
        }
    },
    methods: {
        nextpage() {
            this.$emit('next-page');
        },
        backToMenu () {
            this.$emit('chapters-page');
        },
        showText(event) {
            this.pressedIndex = Number(event.target.id);
            console.log(event.target.id);
            if (this.textVis === false) {
                this.textVis = true;
            } else {
                this.textVis = false
            }
        }
    },
    computed: {
    titleName() {
      // Ensure index is within bounds
      const titles = json.chapters[0].titles;
      return titles[this.title - 1] || 'Unknown Title';
    },
    subtitels() {
      // Ensure subtitle key exists and is an array
      const subtitleKey = `chpt${this.title}-sub`;
      const subtitles = json.chapters[0][subtitleKey];
      return Array.isArray(subtitles) ? subtitles : [];
    }
  }
}
</script>

<style>
#bookBtn {
    top: 1%;
    right: 5%;
    height: auto;
    width: 23%;
}

#title {
    top: -2%;
    color: #F07067;
    right: 5%;
    font-size: 400%;
}

.main {
    position: absolute;
    top: 15%;
    right: 50%;
    transform: translateX(50%);
    background: url("@/assets/images/mainBackground.png");
    background-size: 100% 100%;
    height: 80vh;
    width: 90vw;
    /*  */
}



.subtitleName {
    margin-top: 3%;
    width: 92%;
    height: auto;
    border-radius: 3vw;
    background-color: #F07067;
    right: 48%;
    transform: translateX(50%);
    z-index: 100;
    color: #FEE7D6;
    text-align: right;
    font-size: 7.5vw;
    position: relative;
    top: 5%;
    cursor: pointer;
}

.spacing {
    /* border: 1px black solid; */
    top: 1%;
    right: 50%;
    transform: translateX(50%);
    height: 76vh;
    width: 87.5vw;
}

</style>