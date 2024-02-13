<template>
  <h1>{{ country }} 2023</h1>
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
          type: "Erneuerbar",
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
          type: "Konventionell",
          data: [
            { name: 'Erdgas', color: 'orange', value: 4.43 },
            { name: 'Andere', color: 'grey', value: 0.03 },
          ]
        },
        {
          type: "Speicher",
          data: [
            { name: 'Pumpspeicher', color: 'darkblue', value: 3.71 },
          ]
        },
        {
          type: "Last",
          data: [
            { name: 'Min', color: 'black', value: 4.7 },
            { name: 'Max-Min', color: 'darkgrey', value: 2.55 },
          ]
        }
      ],
      Spanien: [
        {
          type: "Erneuerbar",
          data: [
            { name: 'Wind an Land', color: 'green', value: 30.16 },
            //{ name: 'Wind auf See', color: 'lightgreen', value: 0.0 },
            { name: 'Laufwasser', color: 'lightblue', value: 1.15 },
            { name: 'Solar', color: '#ddce25', value: 23.87 },
            { name: 'Speicherwasser', color: 'blue', value: 15.77 },
            { name: 'Biomasse', color: 'pink', value: 0.71 },
            { name: 'Müll', color: 'magenta', value: 0.55 },
          ]
        },
        {
          type: "Konventionell",
          data: [
            { name: 'Erdgas', color: 'orange', value: 29.87 },
            { name: 'Kernenergie', color: 'red', value: 7.12 },
            { name: 'Steinkohle', color: '#631313', value: 3.22 },
            { name: 'Öl', color: '#252525', value: 0.7 },
            { name: 'Andere', color: 'grey', value: 0.12 },
          ]
        },
        {
          type: "Speicher",
          data: [
            { name: 'Pumpspeicher', color: 'darkblue', value: 3.42 },
          ]
        },
        {
          type: "Last",
          data: [
            { name: 'Min', color: 'black', value: 19.19 },
            { name: 'Max-Min', color: 'darkgrey', value: 12.64 },
          ]
        }
      ],
      Italien: [
        {
          type: "Erneuerbar",
          data: [
            { name: 'Wind an Land', color: 'green', value: 11.65 },
            { name: 'Wind auf See', color: 'lightgreen', value: 0.03 },
            { name: 'Laufwasser', color: 'lightblue', value: 10.29 },
            { name: 'Solar', color: '#ddce25', value: 5.93 },
            { name: 'Speicherwasser', color: 'blue', value: 4.54 },
            { name: 'Biomasse', color: 'pink', value: 1.54 },
            { name: 'Geothermie', color: 'brown', value: 0.87 },
          ]
        },
        {
          type: "Konventionell",
          data: [
            { name: 'Erdgas', color: 'orange', value: 45.16 },
            { name: 'Steinkohle', color: '#631313', value: 5.58 },
            { name: 'Kohlegas', color: '#422222', value: 2.57 },
            { name: 'Öl', color: '#252525', value: 1.56 },
            { name: 'Andere', color: 'grey', value: 0.33 },
          ]
        },
        {
          type: "Speicher",
          data: [
            { name: 'Pumpspeicher', color: 'darkblue', value: 7.26 },
          ]
        },
        {
          type: "Last",
          data: [
            { name: 'Min', color: 'black', value: 21.0 },
            { name: 'Max-Min', color: 'darkgrey', value: 19.52 },
          ]
        }
      ],
      Frankreich: [
        {
          type: "Erneuerbar",
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
          type: "Konventionell",
          data: [
            { name: 'Öl', color: '#252525', value: 3.04 },
            { name: 'Kernenergie', color: 'red', value: 61.37 },
            { name: 'Steinkohle', color: '#631313', value: 1.81 },
            { name: 'Erdgas', color: 'orange', value: 13.13 },
            { name: 'Andere', color: 'grey', value: 1.03 },
          ]
        },
        {
          type: "Speicher",
          data: [
            { name: 'Pumpspeicher', color: 'darkblue', value: 5.06 },
          ]
        },
        {
          type: "Last",
          data: [
            { name: 'Min', color: 'black', value: 38.32 },
            { name: 'Max-Min', color: 'darkgrey', value: 22.09 },
          ]
        }
      ],
      Dänemark: [
        {
          type: "Erneuerbar",
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
          type: "Konventionell",
          data: [
            { name: 'Erdgas', color: 'orange', value: 1.57 },
            { name: 'Steinkohle', color: '#631313', value: 3.02 },
            { name: 'Öl', color: '#252525', value: 0.96 },
          ]
        },
        {
          type: "Speicher",
          data: [
          ]
        },
        {
          type: "Last",
          data: [
            { name: 'Min', color: 'black', value: 3.03 },
            { name: 'Max-Min', color: 'darkgrey', value: 1.62 },
          ]
        }
      ],
      Norwegen: [
        {
          type: "Erneuerbar",
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
          type: "Konventionell",
          data: [
            { name: 'Erdgas', color: 'orange', value: 0.47 },
            { name: 'Andere', color: 'grey', value: 0.03 },
          ]
        },
        {
          type: "Speicher",
          data: [
            { name: 'Pumpspeicher', color: 'darkblue', value: 1.06 },
          ]
        },
        {
          type: "Last",
          data: [
            { name: 'Min', color: 'black', value: 13.8 },
            { name: 'Max-Min', color: 'darkgrey', value: 2.75 },
          ]
        }
      ],
      Schweden: [
        {
          type: "Erneuerbar",
          data: [
            { name: 'Speicherwasser', color: 'blue', value: 16.3 },
            { name: 'Wind an Land', color: 'green', value: 16.7 },
            //{ name: 'Wind auf See', color: 'lightgreen', value: 0.0 },
            { name: 'Solar', color: '#ddce25', value: 3.2 },
          ]
        },
        {
          type: "Konventionell",
          data: [
            { name: 'Kernenergie', color: 'red', value: 6.9 },
            { name: 'Andere', color: 'grey', value: 6.6 },
          ]
        },
        {
          type: "Speicher",
          data: [
          ]
        },
        {
          type: "Last",
          data: [
            { name: 'Min', color: 'black', value: 12.76 },
            { name: 'Max-Min', color: 'darkgrey', value: 3.79 },
          ]
        }
      ],
      Finnland: [
        {
          type: "Erneuerbar",
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
          type: "Konventionell",
          data: [
            { name: 'Kernenergie', color: 'red', value: 4.36 },
            { name: 'Erdgas', color: 'orange', value: 1.74 },
            { name: 'Steinkohle', color: '#631313', value: 1.41 },
            { name: 'Öl', color: '#252525', value: 1.05 },
            { name: 'Torf', color: '#254525', value: 1.04 },
            { name: 'Andere', color: 'grey', value: 0.45 },
          ]
        },
        {
          type: "Speicher",
          data: [
          ]
        },
        {
          type: "Last",
          data: [
            { name: 'Min', color: 'black', value: 7.86 },
            { name: 'Max-Min', color: 'darkgrey', value: 1.55 },
          ]
        }
      ],
      Deutschland: [
        {
          type: "Erneuerbar",
          data: [
            { name: 'Laufwasser', color: 'lightblue', value: 4.94 },
            { name: 'Wind an Land', color: 'green', value: 61.03 },
            { name: 'Wind auf See', color: 'lightgreen', value: 8.46 },
            { name: 'Solar', color: '#ddce25', value: 81.82 },
            { name: 'Biomasse', color: 'pink', value: 9.03 },
          ]
        },
        {
          type: "Konventionell",
          data: [
            { name: 'Erdgas', color: 'orange', value: 34.8 },
            { name: 'Steinkohle', color: '#631313', value: 18.94 },
            { name: 'Braunkohle', color: '#422222', value: 18.55 },
            { name: 'Mineralöl', color: '#252525', value: 4.68 },
            { name: 'Andere', color: 'grey', value: 0.33 },
          ]
        },
        {
          type: "Speicher",
          data: [
            { name: 'Pumpspeicher', color: 'darkblue', value: 9.7 },
            { name: 'Batteriespeicher', color: 'silver', value: 7.88 },
          ]
        },
        {
          type: "Last",
          data: [
            { name: 'Min', color: 'black', value: 36.8 },
            { name: 'Max-Min', color: 'darkgrey', value: 26.9 },
          ]
        }
      ],
    };

    if (data[props.country] == undefined) {
      console.log(`No data for country ${props.country} available.`);
      return;
    }

    const max = data[props.country].map(cat => cat.data).flat().reduce(function(prev, current) {
      return (prev && prev.value > current.value) ? prev : current;
    }).value;

    if (canvas.value) {
      new Chart(
        canvas.value,
        {
          type: 'bar',
          data: {
            labels: data[props.country].map(cat => cat.type),
            datasets: data[props.country].map((cat, index) => cat.data.map(entry => ({
                label: entry.name,
                data: [index == 0 ? entry.value : 0, index == 1 ? entry.value : 0, index == 2 ? entry.value : 0, index == 3 ? entry.value : 0],
                backgroundColor: entry.color,
            }))).flat()
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
