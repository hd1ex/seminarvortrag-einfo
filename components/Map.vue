<template>
  <div class="map" ref="mapContainer"></div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import L from 'leaflet';
import { shallowRef, onMounted, onUnmounted, markRaw } from 'vue';

export default {
  name: "Map",
  props: {
    country: String,
  },
  setup (props) {
    const mapContainer = shallowRef(null);
    const map = shallowRef(null);

    onMounted(() => {
      map.value = L.map(mapContainer.value).setView([51.6, 12.0], 5.0);
      /*
      const tiles = L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
      	maxZoom: 19,
      	attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
      }).addTo(map.value);
      */

      fetch('/seminarvortrag-einfo/countries.geojson')
        .then((response) => response.json())
        .then((json) => {
          function style(feature) {
            let highlight = feature.properties.wind_2023 !== undefined ? 255 : 0;
            if (feature.properties.NAME_DE === props.country) {
              let coords = [feature.properties.LABEL_Y, feature.properties.LABEL_X];
              map.value.flyTo(coords);

              var tooltip = L.tooltip(coords, {content: `
              <b>${feature.properties.NAME_DE}</b>
          <table>
          <thead>
            <tr>
              <th>Jahr</th>
              <th>Wind</th>
              <th>PV</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><b>2023</b></td>
              <td>${feature.properties.wind_2023}&#8239;GW</td>
              <td>${feature.properties.pv_2023}&#8239;GW</td>
            </tr>
            <tr>
              <td><b>2030</b></td>
              <td>${feature.properties.wind_2030}&#8239;GW</td>
              <td>${feature.properties.pv_2030}&#8239;GW</td>
            </tr>
          </tbody>
          </table>
          `,
                direction: feature.properties.tooltip_dir ?? 'auto'
              })
                ;//.addTo(map.value);
            }

            return {
              fillColor: `rgb(0, ${highlight}, 0)`,
              weight: 2,
              opacity: 1,
              color: 'white',
              dashArray: '3',
              fillOpacity: 0.7
            };
          }
          L.geoJson(json, {style: style}).addTo(map.value);
        });
    }),
      onUnmounted(() => {
        map.value?.remove();
      })

    return {
      map, mapContainer
    };
  }
};
</script>


<style scoped>
.map {
  position: absolute;
  width: 98%;
  height: 100%;
}
</style>
