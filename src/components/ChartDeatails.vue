<script setup>
import BarChart from './BarChart.vue';
</script>
<template>
  <div class="detail-card">
    <h3>Spending - Last 7 days</h3>
    <BarChart />
    <div class="total">
      <div class="first">
        <p>Total this month</p>
        <h2>$478.33</h2>
      </div>
      <div class="second">
        <p style="color: black;">+27</p>
        <p>from last month</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .detail-card{
    max-width: 400px;
    width: 100%;
    background-color: white;
    padding: 20px 40px;
    margin-top: 1.5rem;
    border-radius: 5px;
    margin-bottom: 2rem;
  }

  .detail-card>h3{
    margin-bottom: 2rem;
    color: hsl(25, 47%, 15%);
  }

  .total{
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    margin-top: 2rem;
    border-top: 1px solid hsl(28, 10%, 53%);
  }

  .first{
    margin-top: 2rem;
  }
  .first>p{
    color: hsl(28, 10%, 53%);
    margin-bottom: 0.5rem;
  }

  .second>p{
    color: hsl(28, 10%, 53%);
    font-size: 0.8rem;
    text-align: right;
  }
</style>