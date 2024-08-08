<template>
  <div class="screen"> 
    <div>
      <img src="@/assets/images/pele.png" id="pele"/>
      <img src="@/assets/images/gapa.png" id="gapa"/>
      <img src="@/assets/images/bislach.png" id="bislach"/>
    </div>

    <first-page v-if="page === 1" @next-page="nextpage" class="page"></first-page> 
    <explenations v-if="page === 2" class="page" @next-page="nextpage" :secondLook="secondLookExp"></explenations>
    <!-- <head-content class="page" v-if="page === 3"></head-content> -->
    <chapters v-if="page === 3" @next-page="nextpage" class="page" @backToExp="backToExp"></chapters>
  </div>
</template>

<script>
import Explenations from '@/components/Explenations.vue';
import FirstPage from '@/components/FirstPage.vue';
import HeadContent from '@/components/HeadContent.vue';
import Chapters from '@/components/chapters.vue';

export default {
  name: "app",
  components: {
    Explenations,
    FirstPage,
    HeadContent,
    Chapters
  },
  data () {
    return {
      page: 1,
      secondLookExp: false
    }
  },
  methods: {
    nextpage() {
      this.page++
    },
    backToExp() {
      this.secondLookExp = true;
      this.page = 2;
    }
  }
};
</script>

<style>
@font-face {
  font-family: "aduma";
  src: url("@/assets/fonts/Aduma Regular.ttf");
}

* {
  font-family: "aduma";
  direction: rtl;
  overflow-x: hidden;
}

.screen {
	background: linear-gradient(-45deg, #006D77, #00A896, #05668D, #028090, #006D77);
	background-size: 400% 400%;
	animation: gradient 5s ease infinite;
  width: 100%;
	height: 100vh;
  }

.page {
  width: 100%;
	height: 100vh;
}

  #bislach {
    position: relative;
    right: 30%;
    width: 12%;
    height: auto;
  }

  #gapa {
    position: relative;
    right: 22%;
    width: 19%;
    height: auto;
  }

  #pele {
    position: relative;
    width: 35%;
    right: -5%;
    height: auto;
  }

  @keyframes gradient {
    0% {
      background-position: 0% 50%;
    }
    50% {
      background-position: 100% 50%;
    }
    100% {
      background-position: 0% 50%;
    }
  }
</style>