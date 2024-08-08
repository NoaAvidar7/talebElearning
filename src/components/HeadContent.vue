<template>
  <div class="container">
    <div class="sliding-background"></div>
    <div class="blank">
      <img id="back" src="@/assets/images/back.png" @click="back" />
      <div class="head">
        {{head}}
      </div>
      <div class="text" :style="{'font-size': sizeFont}">
        {{text}}
      </div>
      <img id="next" src="@/assets/images/nextArrow.png" />
    </div>
  </div>
</template>

<script>
import json from "../../text.json"

export default {
    name: "head-content",
    props: ["textType"],
    data () {
      return {
        head: json["headText"][0][this.textType][0],
        text: json["headText"][0][this.textType][1],
        sizeFont: '212%',
        currType: this.textType
      }
    },
    methods: {
      back () {
        this.$emit('back');
      },
    },
    computed: {
      changeFont () {
        if (this.currType !== "whatIsIt") {
          this.sizeFont = '243%'
        }
      }
    }
}
</script>

<style>
.container {
  overflow: hidden;
}

.sliding-background {
  background: url("@/assets/images/pattern1.png");
  background-size: 100% 50%;
  height: 100vh;
  width: 100vw;
  animation: upward 15s linear infinite;
  z-index: 10;
}

.blank {
  position: absolute;
  top: 4%;
  right: 50%;
  transform: translateX(50%);
  background: url("@/assets/images/blankPage.png");
  background-size: 100% 100%;
  height: 80vh;
  width: 90vw;
  z-index: 20;
}

.text {
  text-shadow: 3px 3px 5px #4b4b4b36;
  text-align: right;
  color: #E26B5C;
  top: 3%;
  right: 11.5%;
  height: 70%;
  width: 85%;
}

.head {
  color: #C33D54;
  text-shadow: 3px 3px 5px #4b4b4b71;
  top: 15%;
  right: 55%;
  transform: translate(50%, -50%);
  height: 15%;
  width: 85%;
  font-size: 270%;
}

#back {
  position: absolute;
  top: 0%;
  left: 2%;
  height: auto;
  width: 8%;
}

#next {
  position: absolute;
  bottom: 2%;
  left: 10%;
  height: auto;
  width: 13%;
}

@keyframes upward {
  from {
    background-position: 0% 0%;
  }
  to {
    background-position: 0% -100%;
  }
}


</style>