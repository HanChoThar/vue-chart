<script setup>
import Balance from './components/Balance.vue';
import ChartDeatails from './components/ChartDeatails.vue';

</script>

<template>
    <div class="main">
      <Balance/>
      <ChartDeatails />
    </div>
</template>

<style>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;

}
#app{
  font-family: sans-serif;
  background-color: hsl(27, 66%, 92%);
}

.main {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin: 0 3rem;
}

</style>
