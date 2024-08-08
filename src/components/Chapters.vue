<template>
  <div>
    <div class="headline2" v-if="!showcontent"> תו תקן איכות בהכשרה </div>
    <div class="container-chpt" v-if="!showcontent">
      <div v-for="index in 6" :key="index" class="chpt">
        <img
          :src="`./chpt${index}.png`" 
          :id="index"
          class="img-chpt"
          @click="chptChosen(index)"
        />
      </div>
      <div class="space"></div>
    </div>
    
    <content-handler v-if="showcontent" class="page" :title="titleNum" @chapters-page="showcontent = false"></content-handler>
  </div>
</template>

<script>
import ContentHandler from '@/components/ContentHandler.vue';

export default {
  name: "chapters",
  components: {
    ContentHandler,
  },
  data() {
    return {
      showcontent: false,
      titleNum: 0,
    };
  },
  methods: {
    chptChosen(index) {
      if (index <= 5 ) {
        this.showcontent = true;
        this.titleNum = index;
      } else if (index === 6) {
        this.$emit('backToExp', true);
      }
    }, 
  }
};
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

.container-chpt {
  top: 15%;
  position: absolute;
  width: 100%;
  height: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  align-content: space-around;
}

.chpt {
  width: 40%;
  height: 23%;
}

.img-chpt {
  width: 100%;
  height: auto;
}

.space {
  top: 20%;
  height: 20vh;
  margin-bottom: 10rem;
}
</style>