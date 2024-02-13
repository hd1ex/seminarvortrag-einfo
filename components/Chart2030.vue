<template>
  <h1>Ausbau {{ country }}</h1>
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

  const props = defineProps(['country']);

  onMounted(() => {
    let data = {
      Portugal: [
        {
          type: "Erneuerbar 2023",
          data: [
            { name: 'Wind an Land', color: 'green', value: 5.33 },
            { name: 'Wind auf See', color: 'lightgreen', value: 0.02 },
            { name: 'Laufwasser', color: 'lightblue', value: 2.86 },
            { name: 'Solar', color: '#ddce25', value: 1.81 },
            { name: 'Speicherwasser', color: 'blue', value: 1.63 },
            { name: 'Biomasse', color: 'pink', value: 0.68 },
          ]
        },
        {
          type: "Erneuerbar 2030",
          data: [
            { name: 'Wind an Land', color: 'green', value: 10.4 },
            { name: 'Wind auf See', color: 'lightgreen', value: 2.0 },
            { name: 'Laufwasser', color: 'lightblue', value: 2.86 },
            { name: 'Solar', color: '#ddce25', value: 20.40 },
            { name: 'Speicherwasser', color: 'blue', value: 1.63 },
            { name: 'Biomasse', color: 'pink', value: 1.4 },
          ]
        },
        /*
        {
          type: "Konventionell 2023",
          data: [
            { name: 'Erdgas', color: 'orange', value: 4.43 },
            { name: 'Andere', color: 'grey', value: 0.03 },
          ]
        },
        {
          type: "Konventionell 2030",
          data: [
            { name: 'Erdgas', color: 'orange', value: 3.8 },
            { name: 'Andere', color: 'grey', value: 0.4 },
          ]
        },
        */
        {
          type: "Speicher 2030",
          data: [
            { name: 'Pumpspeicher', color: 'darkblue', value: 3.9 },
            { name: 'Batteriespeicher', color: 'silver', value: 1.0 },
          ]
        },
      ],
      Spanien: [
        {
          type: "Erneuerbar 2023",
          data: [
            { name: 'Wind an Land', color: 'green', value: 30.16 },
            //{ name: 'Wind auf See', color: 'lightgreen', value: 0.0 },
            { name: 'Solar', color: '#ddce25', value: 23.87 },
            { name: 'Laufwasser', color: 'lightblue', value: 1.15 },
            { name: 'Speicherwasser', color: 'blue', value: 15.77 },
            { name: 'Biomasse', color: 'pink', value: 0.71 },
            { name: 'Müll', color: 'magenta', value: 0.55 },
          ]
        },
        {
          type: "Erneuerbar 2030",
          data: [
            { name: 'Wind an Land', color: 'green', value: 57.51 },
            { name: 'Wind auf See', color: 'lightgreen', value: 2.8 },
            { name: 'Solar', color: '#ddce25', value: 72.75 },
            { name: 'Laufwasser', color: 'lightblue', value: 1.15 },
            { name: 'Speicherwasser', color: 'blue', value: 15.77 },
            { name: 'Biomasse', color: 'pink', value: 0.71 },
            { name: 'Müll', color: 'magenta', value: 0.55 },
          ]
        },
        /*
        {
          type: "Konventionell 2023",
          data: [
            { name: 'Erdgas', color: 'orange', value: 29.87 },
            { name: 'Kernenergie', color: 'red', value: 3},
            { name: 'Öl', color: '#252525', value: 0.7 },
            { name: 'Andere', color: 'grey', value: 0.12 },
          ]
        },
        {
          type: "Konventionell 2030",
          data: [
            { name: 'Erdgas', color: 'orange', value: 24.5 },
            { name: 'Kernenergie', color: 'red', value: 3},
          ]
        },
        */
        {
          type: "Speicher 2030",
          data: [
            { name: 'Speicher', color: 'grey', value: 17.6 },
          ]
        },
      ],
      Italien: [
        {
          type: "Erneuerbar 2023",
          data: [
            { name: 'Speicherwasser', color: 'blue', value: 4.54 },
            { name: 'Wind an Land', color: 'green', value: 11.65 },
            { name: 'Wind auf See', color: 'lightgreen', value: 0.03 },
            { name: 'Laufwasser', color: 'lightblue', value: 10.29 },
            { name: 'Solar', color: '#ddce25', value: 5.93 },
            { name: 'Biomasse', color: 'pink', value: 1.54 },
            { name: 'Geothermie', color: 'brown', value: 0.87 },
          ]
        },
        {
          type: "Erneuerbar 2030",
          data: [
            { name: 'Speicherwasser', color: 'blue', value: 4.54 },
            { name: 'Wind an Land', color: 'green', value: 26.04 },
            { name: 'Wind auf See', color: 'lightgreen', value: 2.1 },
            { name: 'Laufwasser', color: 'lightblue', value: 10.29 },
            { name: 'Solar', color: '#ddce25', value: 79.92 },
            { name: 'Biomasse', color: 'pink', value: 3.0 },
            { name: 'Geothermie', color: 'brown', value: 1.0 },
          ]
        },
      ],
      Frankreich: [
        {
          type: "Erneuerbar 2023",
          data: [
            { name: 'Wind an Land', color: 'green', value: 22.13 },
            { name: 'Wind auf See', color: 'lightgreen', value: 1.48 },
            { name: 'Laufwasser', color: 'lightblue', value: 11.6 },
            { name: 'Biomasse', color: 'pink', value: 1.4 },
            { name: 'Solar', color: '#ddce25', value: 17.42 },
            { name: 'Speicherwasser', color: 'blue', value: 8.79 },
            { name: 'Meeresenergie', color: 'lightblue', value: 0.24 },
            { name: 'Müll', color: 'magenta', value: 0.97 },
          ]
        },
        {
          type: "Erneuerbar 2030",
          data: [
            { name: 'Wind an Land', color: 'green', value: 35 },
            { name: 'Wind auf See', color: 'lightgreen', value: 3.6 },
            { name: 'Laufwasser', color: 'lightblue', value: 11.6 },
            { name: 'Biomasse', color: 'pink', value: 1.4 },
            { name: 'Solar', color: '#ddce25', value: 60 },
            { name: 'Speicherwasser', color: 'blue', value: 8.79 },
            { name: 'Meeresenergie', color: 'lightblue', value: 0.24 },
            { name: 'Müll', color: 'magenta', value: 0.97 },
          ]
        },
      ],
      Dänemark: [
        {
          type: "Erneuerbar 2023",
          data: [
            { name: 'Laufwasser', color: 'lightblue', value: 0.01 },
            { name: 'Wind an Land', color: 'green', value: 4.71 },
            { name: 'Wind auf See', color: 'lightgreen', value: 2.31 },
            { name: 'Solar', color: '#ddce25', value: 2.32 },
            { name: 'Müll', color: 'magenta', value: 0.38 },
            { name: 'Biomasse', color: 'pink', value: 1.75 },
            { name: 'Andere Erneuerbare', color: 'cyan', value: 0.14 },
          ]
        },
        {
          type: "Erneuerbar 2030",
          data: [
            { name: 'Laufwasser', color: 'lightblue', value: 0.01 },
            { name: 'Wind an Land', color: 'green', value: 5.9 },
            { name: 'Wind auf See', color: 'lightgreen', value: 9 },
            { name: 'Solar', color: '#ddce25', value: 11.7 },
            { name: 'Müll', color: 'magenta', value: 0.38 },
            { name: 'Biomasse', color: 'pink', value: 1.75 },
            { name: 'Andere Erneuerbare', color: 'cyan', value: 0.14 },
          ]
        },
      ],
      Norwegen: [
        {
          type: "Erneuerbar 2023",
          data: [
            { name: 'Speicherwasser', color: 'blue', value: 26.66 },
            { name: 'Laufwasser', color: 'lightblue', value: 6.88 },
            { name: 'Wind an Land', color: 'green', value: 5.13 },
            //{ name: 'Wind auf See', color: 'lightgreen', value: 0.0 },
            { name: 'Solar', color: '#ddce25', value: 0.01 },
            { name: 'Müll', color: 'magenta', value: 0.09 },
            { name: 'Biomasse', color: 'pink', value: 0.01 },
            { name: 'Andere Erneuerbare', color: 'cyan', value: 0.1 },
          ]
        },
        {
          type: "Erneuerbar 2040",
          data: [
            { name: 'Speicherwasser', color: 'blue', value: 26.66 },
            { name: 'Laufwasser', color: 'lightblue', value: 6.88 },
            { name: 'Wind an Land', color: 'green', value: 5.13 },
            { name: 'Wind auf See', color: 'lightgreen', value: 30.0 },
            { name: 'Solar', color: '#ddce25', value: 0.01 },
            { name: 'Müll', color: 'magenta', value: 0.09 },
            { name: 'Biomasse', color: 'pink', value: 0.01 },
            { name: 'Andere Erneuerbare', color: 'cyan', value: 0.1 },
          ]
        },
      ],
      Schweden: [
        {
          type: "Erneuerbar 2023",
          data: [
            { name: 'Speicherwasser', color: 'blue', value: 16.3 },
            { name: 'Wind an Land', color: 'green', value: 16.7 },
            //{ name: 'Wind auf See', color: 'lightgreen', value: 0.0 },
            { name: 'Solar', color: '#ddce25', value: 3.2 },
          ]
        },
        {
          type: "Erneuerbar 2030",
          data: [
            { name: 'Speicherwasser', color: 'blue', value: 16.3 },
            { name: 'Wind an Land', color: 'green', value: 21.7 },
            //{ name: 'Wind auf See', color: 'lightgreen', value: 0.0 },
            { name: 'Solar', color: '#ddce25', value: 5.2 },
          ]
        },
      ],
      Finnland: [
        {
          type: "Erneuerbar 2023",
          data: [
            { name: 'Laufwasser', color: 'lightblue', value: 3.17 },
            { name: 'Wind an Land', color: 'green', value: 6.62 },
            //{ name: 'Wind auf See', color: 'lightgreen', value: 0.0 },
            { name: 'Müll', color: 'magenta', value: 0.09 },
            { name: 'Solar', color: '#ddce25', value: 0.03 },
            { name: 'Biomasse', color: 'pink', value: 1.7 },
            { name: 'Andere Erneuerbare', color: 'cyan', value: 0.39 },
          ]
        },
        {
          type: "Erneuerbar 2030",
          data: [
            { name: 'Laufwasser', color: 'lightblue', value: 3.17 },
            { name: 'Wind an Land', color: 'green', value: 6.62 },
            { name: 'Wind auf See', color: 'lightgreen', value: 1.3 },
            { name: 'Müll', color: 'magenta', value: 0.09 },
            { name: 'Solar', color: '#ddce25', value: 0.03 },
            { name: 'Biomasse', color: 'pink', value: 1.7 },
            { name: 'Andere Erneuerbare', color: 'cyan', value: 0.39 },
          ]
        },
      ],
      Deutschland: [
        {
          type: "Erneuerbar 2023",
          data: [
            { name: 'Laufwasser', color: 'lightblue', value: 4.94 },
            { name: 'Wind an Land', color: 'green', value: 61.03 },
            { name: 'Wind auf See', color: 'lightgreen', value: 8.46 },
            { name: 'Solar', color: '#ddce25', value: 81.82 },
            { name: 'Biomasse', color: 'pink', value: 9.03 },
          ]
        },
        {
          type: "Erneuerbar 2030",
          data: [
            { name: 'Laufwasser', color: 'lightblue', value: 4.94 },
            { name: 'Wind an Land', color: 'green', value: 115 },
            { name: 'Wind auf See', color: 'lightgreen', value: 30 },
            { name: 'Solar', color: '#ddce25', value: 215 },
            { name: 'Biomasse', color: 'pink', value: 8.4 },
          ]
        },
      ],
    };

    if (data[props.country] == undefined) {
      console.log(`No data for country ${props.country} available.`);
      return;
    }

    if (canvas.value) {
      const max = data[props.country].map(cat => cat.data).flat().reduce(function(prev, current) {
        return (prev && prev.value > current.value) ? prev : current;
      }).value;

      let datasets = {};

      data[props.country].forEach((cat, index) => {
        cat.data.forEach(entry => {
          if (datasets[entry.name] == undefined) {
            let values = [];
            for(let i = 0; i < index; ++i) {
              values.push(0);
            }
            values.push(entry.value);
            datasets[entry.name] = {color: entry.color, values: values};
          } else {
            for(let i = datasets[entry.name].values.length; i <= index; ++i) {
              datasets[entry.name].values.push(0);
            }
            datasets[entry.name].values[index] = entry.value;
          }
        });
      });

      new Chart(
        canvas.value,
        {
          type: 'bar',
          data: {
            labels: data[props.country].map(cat => cat.type),
            datasets: Object.keys(datasets).map(name => ({
                label: name,
                data: datasets[name].values,
                backgroundColor: datasets[name].color,
            }))
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
                  return value > max / 15 ? value + ' GW' : '';
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
