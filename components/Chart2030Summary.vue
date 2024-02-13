<template>
  <div class='chart'>
    <canvas ref='canvas'></canvas>
  </div>
</template>

<script setup>
  import { shallowRef, onMounted, onUnmounted, markRaw } from 'vue';
  import Chart from 'chart.js/auto';
  import ChartDataLabels from 'chartjs-plugin-datalabels';
  Chart.register(ChartDataLabels);
  Chart.defaults.font.size = 30;

  const chart = shallowRef(null);
  const canvas = shallowRef();

  onMounted(() => {
    let datasets = [
      {
        label: 'Wind 2023',
        data: [
          //{ country: 'Deutschland', value: 69.49 },
          { country: 'Italien', value: 11.68 },
          { country: 'Frankreich', value: 23.61 },
          { country: 'Spanien', value: 30.16 },
          { country: 'Portugal', value: 5.52 },
          { country: 'Norwegen', value: 5.13 },
          { country: 'Schweden', value: 16.7 },
          { country: 'Dänemark', value: 7.02 },
          { country: 'Finnland', value: 6.62 },
        ],
        backgroundColor: 'blue',
      },
      {
        label: 'Photovoltaik 2023',
        data: [
          //{ country: 'Deutschland', value: 81.82 },
          { country: 'Italien', value: 5.93 },
          { country: 'Frankreich', value: 17.42 },
          { country: 'Spanien', value: 23.87 },
          { country: 'Portugal', value: 1.81 },
          { country: 'Norwegen', value: 0.01 },
          { country: 'Schweden', value: 3.2 },
          { country: 'Dänemark', value: 2.32 },
          { country: 'Finnland', value: 0.03 },
        ],
        backgroundColor: '#ddce25',
      },
      {
        label: 'Ausbau Wind 2030',
        data: [
          //{ country: 'Deutschland', value: 75.51 },
          { country: 'Italien', value: 16.32 },
          { country: 'Frankreich', value: 14.99 },
          { country: 'Spanien', value: 19.84 },
          { country: 'Portugal', value: 10 },
          { country: 'Norwegen', value: 30.0 },
          { country: 'Schweden', value: 5 },
          { country: 'Dänemark', value: 7.88 },
          { country: 'Finnland', value: 1.3 },
        ],
        backgroundColor: 'lightblue',
      },
      {
        label: 'Ausbau Photovoltaik 2030',
        data: [
          //{ country: 'Deutschland', value: 133.18 },
          { country: 'Italien', value: 74.07 },
          { country: 'Frankreich', value: 42.58 },
          { country: 'Spanien', value: 15.13 },
          { country: 'Portugal', value: 18.6 },
          { country: 'Norwegen', value: 0 },
          { country: 'Schweden', value: 2 },
          { country: 'Dänemark', value: 9.38 },
          { country: 'Finnland', value: 0.0 },
        ],
        backgroundColor: 'orange',
      },
    ];

    if (canvas.value) {
      /*
      const max = data[props.country].map(cat => cat.data).flat().reduce(function(prev, current) {
        return (prev && prev.value > current.value) ? prev : current;
      }).value;
      */

      new Chart(
        canvas.value,
        {
          type: 'bar',
          data: {
            labels: datasets[0].data.map(c => c.country),
            datasets: datasets.map(cat => ({
              label: cat.label,
              data: cat.data.map(e => e.value),
              backgroundColor: cat.backgroundColor,
            })),
          },
          options: {
            plugins: {
              datalabels: {
                color: '#EEEEEE',
                textStrokeWidth: 1,
                //font: {size: 20},
                textShadowBlur: 11,
                textShadowColor: '#000000',
                //backgroundColor: '#111111',
                formatter: (value) => {
                  return value > 5.5 ? value + ' GW' : '';
                }
              }
            },
            scales: {
              x: {
                stacked: true,
              },
              y: {
                stacked: true
              }
            }
          }
        }
      );
    }
  }),
  onUnmounted(() => {
    canvas.value?.remove();
  })
</script>

<style scoped>
.chart {
  height: 80%;
  margin-top: 3em;
}
</style>
