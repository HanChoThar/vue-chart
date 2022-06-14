<script>
import data from '../../data.json';
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

let days = data.map(e => e.day);
let amounts = data.map(a => a.amount);
function argMax(array) {
  return array.map((x, i) => [x, i]).reduce((r, a) => (a[0] > r[0] ? a : r))[1];
}

var color = amounts.map(x => 'hsl(10, 79%, 65%)');

// change max color
color[argMax(amounts)] = 'hsl(186, 34%, 60%)';
export default {
  name: 'BarChart',
  components: { Bar },
  props: {
    chartId: {
      type: String,
      default: 'bar-chart'
    },
    datasetIdKey: {
      type: String,
      default: 'label'
    },
    width: {
      type: Number,
      default: 300
    },
    height: {
      type: Number,
      default: 200
    },
    cssClasses: {
      default: '',
      type: String
    },
    styles: {
      type: Object,
      default: () => {}
    },
    plugins: {
      type: Object,
      default: () => {}
    }
  },
  data() {
    return {
      chartData: {
        labels: days,
        datasets: [ { 
          data: amounts,
          backgroundColor: color,
          borderRadius: 5
        } ],
      },
      chartOptions: {
        scales: {
          x: {
            grid: {
              display: false,
            }
          },
          y: {
            display: false,
          }
        },
        plugins: {
          legend: {
            display: false
          },
          tooltip: {
            enabled: true,
            xAlign: 'center',
            yAlign: 'bottom',
            displayColors: false,
            callbacks: {
              title: function() {
                return '';
              },
              label: function(context) {
                let label = context.dataset.label ||'';
                if(label){
                  label += ' ';
                }
                if (context.parsed.y !== null) {
                            label += new Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD' }).format(context.parsed.y);
                        }
                    return label;
              }
            }
          }
        }
      }
    }
  },
}
</script>

<template>
<div class="container">
  <Bar
    :chart-options="chartOptions"
    :chart-data="chartData"
    :chart-id="chartId"
    :dataset-id-key="datasetIdKey"
    :plugins="plugins"
    :css-classes="cssClasses"
    :styles="styles"
    :width="width"
    :height="height"
  />
</div>
</template>

<style>

  .container {
    display: flex;
    justify-content: center;
  }
</style>