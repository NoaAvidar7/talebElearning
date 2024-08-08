<template>
    <div>
        <div class="headline"> תו תקן איכות בהכשרה </div>
        <div class="explenation">להתחלת הלומדה לחצו על הספרים</div>
        <img src="@/assets/images/lightArraow.png" class="arrow bounce"/>
        <img src="@/assets/images/books2.png" id="books" @click="nextpage"/>
    </div>
  
</template>

<script>
export default {
    name: "first-page",
    methods: {
        nextpage() {
            this.$emit('next-page');
        }
    }
}
</script>

<style>
#books {
    position: absolute;
    bottom: 16%;
    width: 80%;
    height: auto;
    right: 50%;
    transform: translateX(50%);
}

.headline {
    line-height: 120%;
    top: 3%;
    right: 50%;
    transform: translateX(50%);
    text-align: center;
    width: 80%;
    font-size: 520%;
    color: #E29578;
}

.explenation {
    top: 6%;
    right: 50%;
    transform: translateX(50%);
    text-align: center;
    font-size: 135%;
    color: #FFDDD2;
    font-weight: bolder;
}

.arrow{
    position: relative;
    top: 11%;
    right: 48%;
    transform: translateX(50%);
    width: 7%;
    height: auto;
}

.bounce {
  animation: bounce 2s infinite;
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% {
    transform: translateY(0);
  }
  40% {
    transform: translateY(-30px);
  }
  60% {
    transform: translateY(-15px);
  }
}

</style>