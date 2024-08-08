<template>
  <div>
    <div v-if="contentpage === 1" class="page">
      <div class="headline2"> תו תקן איכות בהכשרה </div>
      <img src="@/assets/images/whatIsIt1.png" id="whatIsIt" @click="showContent"/>
      <img src="@/assets/images/meaning1.png" id="meaning" @click="showContent"/>
      <img v-if="counter >= 2 || secondLook" src="@/assets/images/study.png" id="study" @click="nextPage"/>
      <div class="space"></div>
    </div>

    <head-content v-if="contentpage === 2" :textType="clickedExp" @back="HideContent"></head-content>
  </div>
</template>

<script>
import HeadContent from '@/components/HeadContent.vue';

export default {
  components: {     
    HeadContent 
  },
  name: "explenations",
  props:["secondLook"],
  data () {
    return {
      counter: 0,
      contentpage: 1,
      clickedExp: '',
    }
  },
  methods: {
      showContent(event) {
        this.clickedExp = event.currentTarget.id
        this.contentpage++;
        this.counter++;
      },
      HideContent() {
        this.clickedExp = ''
        this.contentpage--;
      },
      nextPage () {
        this.$emit('next-page');
      }

  }
}
</script>

<style>

.headline2 {
    top: 3%;
    right: 50%;
    transform: translateX(50%);
    text-align: center;
    width: 80%;
    font-size: 345%;
    color: #E29578;
}

#whatIsIt {
  right: 47%;
  transform: translateX(50%);
  top: 6%;
  width: 55%;
  height: auto;
}

#meaning {
  right: 47%;
  transform: translateX(50%);
  top: 13%;
  width: 55%;
  height: auto;
}

#study {
  right: 52%;
  transform: translateX(50%);
  top: 19%;
  width: 55%;
  height: auto;
}

.space {
  top: 20%;
  height: 20vh;
  margin-bottom: 10rem;
}
</style>