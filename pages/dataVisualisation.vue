<template>
    <div class="flex">
        <h2 class="text-black font-serif m-2">Data Visualisation</h2>
        <div class="m-2 text-black">
            <vue-easy-pie-chart :percent="percent" :size="330">
            </vue-easy-pie-chart>
        </div>
    </div>
</template>
<script>
import VueEasyPieChart from 'vue-easy-pie-chart'
import 'vue-easy-pie-chart/dist/vue-easy-pie-chart.css'
export default {
    components: {
    VueEasyPieChart 
  },
  created() {
      this.dataVisulisation()
  },
  data() {
      return {
          percent: 0,
          font: "20px"
      };
  },
  methods: {
        dataVisulisation (){ 
            fetch(`https://gorest.co.in/public/v2/users`, { method: 'GET'})
            .then(response => response.json()).then( (data) => {
                console.log('data', data)
                let male = 0;
                let female = 0;
                data.forEach(el => {
                    if (el.gender == 'male') {
                        male++
                    } else {
                        female++
                    }
                });
                this.percent = parseInt((male/(male+female)) * 100)
                console.log(this.percent)
            })
            }
        }
}
</script>