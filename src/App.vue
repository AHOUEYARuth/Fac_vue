<template>
  <div class="app">
    <div id="header"></div>
    <div class="container">
      <div class="content">
        <div class="icon">
          <img src="/src/assets/icon-star.svg" alt="">
          <h1>FAQs</h1>
        </div>
      </div>
      <div class="ask_section">
        <div class="ask_cont" v-for="(item, index) in items" :key="index">
          <div class="ask">
            <span>{{ item.ask }}</span>
            <button type="button" @click="display(index)">
              <img v-if="itemIndex === index" src="/src/assets/icon-minus.svg" alt="">
              <img v-else src="/src/assets/icon-plus.svg" alt="">
            </button>
          </div>
          <span class="ans" v-if="itemIndex == index">{{ item.answer }}</span>
        </div>
      </div>
    </div> 
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
const itemIndex = ref(0)
const items = ref([
  {
    ask: "What is Frontend Mentor, and how will it help me?" , 
    answer: "Frontend Mentor offers realistic coding challenges to help developers improve their frontend coding skills with projects in HTML, CSS, and JavaScript. It's suitable for all levels and ideal for portfolio building."
  },
  {
    ask: 'Is Frontend Mentor free?' ,
    answer: "Yes, Frontend Mentor offers both free and premium coding challenges, with the free option providing access to a range of projects suitable for all skill levels."
  },
  {
    ask: 'Can I use Frontend Mentor projects in my portfolio?',
    answer: "Yes, you can use projects completed on Frontend Mentor in your portfolio. It's an excellent way to showcase your skills to potential employers!"
  },
  {
    ask: "How can I get help if I'm stuck on a Frontend Mentor challenge?" ,
    answer: "The best place to get help is inside Frontend Mentor's Discord community. There's a help channel where you can ask questions and seek support from other community members."
  }
])

function display(index: number) {
  if (itemIndex.value === index) {
    itemIndex.value = 0; 
  } else {
    itemIndex.value = index;
  }
}

</script>


<style scoped>
  .app{
    width: 100%;
    height: 100%;
  }
  #header{
    background-image: url(/src/assets/background-pattern-desktop.svg);
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    height: 45vh;
    width: 100%;
  }
  .container{
    width: 380px;
    background-color: #fff;
    position: absolute;
    top: 55%;
    left: 50%;
    transform: translate(-50%, -50%);
    padding: 0 20px;
    padding-bottom: 20px;
    color: hsl(292, 42%, 14%);
    border-radius: 10px;
    box-shadow: 0px 10px 4px hsl(285, 11%, 93%);
  }
  .content{
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 0;
  }
  .icon{
    display: flex;
    align-items: center;
    gap: 15px;
  }
  .icon img{
    width: 30px;
  }
  h1{
    font-weight: 700;
    font-size: 35px;
  }
  .text_ico{
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  p{
    font-size: 14px;
    color: hsl(292, 16%, 49%);
  }
  h5{
    font-size: 15px;
  }
  .ask{
    list-style: none;
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 13px;
    font-weight: 600;
    margin: 10px 0;
  }
  .ask span{
    cursor: pointer;
  }
  .ask span:hover{
    color: hsl(293, 46%, 54%);
  }
  button{
    border: none;
    background-color: inherit;
    cursor: pointer;
  }
  .ask_cont span{
    font-size: 13px;
  }

  @media screen and (max-width: 425px){
     #header{
      background-image: url(/src/assets/background-pattern-mobile.svg);
      width: 100%;
     }
     .container{
       width: 300px;
     }
   }
   @media screen and (max-width: 375px){
     #header{
      background-image: url(/src/assets/background-pattern-mobile.svg);
      width: 100%;
     }
     .container{
       width: 250px;
     }
   }
</style>
