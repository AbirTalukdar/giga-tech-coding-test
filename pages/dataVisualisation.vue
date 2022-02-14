<template>
    <div class="flex">
        <h2 class="text-black font-serif">Data Visualisation</h2>
        <div class="items-center">
            <vue-easy-pie-chart :percent="6"></vue-easy-pie-chart>
        </div>
    </div>
</template>
<script>
import VueEasyPieChart from 'vue-easy-pie-chart'
import 'vue-easy-pie-chart/dist/vue-easy-pie-chart.css'
export default {
    components: {
    VueEasyPieChart 
  }
}
</script>