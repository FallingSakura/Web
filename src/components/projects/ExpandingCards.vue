<script setup>
import OtherPageView from '@/views/OtherPageView.vue';
import { ref } from 'vue';
const cards = ref([{active: true}, {active: false}, {active: false}, {active: false}, {active: false}])
function fn(index) {
  cards.value.forEach((card, idx) => {
    if (idx === index) {
      card.active = true;
    } else {
      card.active = false;
    }
  })
}
</script>
<template>
  <OtherPageView>
    <template #project>
      <div class="container">
        <div @click="fn(index)" v-for="(card, index) in cards" :key="index" :class="{panel: true, active: card.active}" :id="`p${index + 1}`"><h3>{{ `Pic ${index + 1}` }}</h3></div>
      </div>
    </template>
  </OtherPageView>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Muli&display=swap');

.container {
  font-family: 'Muli', sans-serif;
  display: flex;
  width: 90vw;
  overflow: scroll;
  /* viewport width */
  /* 视口宽度百分比 */
}
.panel {
  position: relative;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  flex: 0.5 0 80px;
  padding: 10px;
  color: #fff;
  border-radius: 50px;
  margin: 10px;
  cursor: pointer;
  height: 75vh;
  /* viewport height */
  transition: all 700ms ease-in;
  box-shadow: 3px 3px 2px 1px hsla(0, 0%, 0%, 0.448);
}

.panel h3 {
  position: absolute;
  bottom: 30px;
  left: 30px;
  margin: 0;
  opacity: 0;
  font-size: 25px;
}
.panel.active {
  flex: 5 0 400px;
}
.panel.active h3 {
  opacity: 1;
  transition: opacity 0.3s ease-in 0.4s;
  /*  */
}

.box {
  width: 80px;
  height: 80px;
  background: #000;
  /* clear: both; */
  position: absolute;
  bottom: 15px;
  left: 90px;
  border-radius: 20%;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2em;
  font-weight: 600;
  transition: all 1000ms ease-out;
  box-shadow: 0 3px 5px 1px black;
  cursor: pointer;
}

.box.boxChanged {
  width: 60px;
  height: 60px;
  font-size: 10px;
  background: #ec7;
  transform: translateX(400px);
  transition: all 700ms ease-in-out;
}


#p1 {
  background-image: url('https://images.unsplash.com/photo-1558979158-65a1eaa08691?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80');
}
#p2 {
  background-image: url('https://images.unsplash.com/photo-1572276596237-5db2c3e16c5d?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80');
}
#p3 {
  background-image: url('https://images.unsplash.com/photo-1507525428034-b723cf961d3e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1353&q=80');
}
#p4 {
  background-image: url('https://images.unsplash.com/photo-1551009175-8a68da93d5f9?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1351&q=80');
}
#p5 {
  background-image: url('https://images.unsplash.com/photo-1549880338-65ddcdfd017b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80');
}

@media (max-width: 480px) {
  .container {
    width: 100vw;
  }
  /* .panel:nth-of-type(4), .panel:nth-of-type(5) {
    display: none;
  } */
}

</style>