<template>
  <div class="map-wrap">
    <div class="map" ref="mapContainer"></div>
  </div>
</template>

<script>
import { Map } from 'maplibre-gl';
import { shallowRef, onMounted, onUnmounted, markRaw } from 'vue';

export default {
  name: "Map",
  props: {
    lng: Number,
    lat: Number,
    zoom: Number,
  },
  setup () {
    const mapContainer = shallowRef(null);
    const map = shallowRef(null);

    onMounted(() => {
      //const props = this.props;
      const props = {lng: 18};

      const initialState = { lng: props.lng, lat: 49.6844, zoom: 3 };

      map.value = markRaw(new Map({
        container: mapContainer.value,
        //style: 'https://demotiles.maplibre.org/style.json',
        style: 'components/assets/style.json',
        center: [initialState.lng, initialState.lat],
        zoom: initialState.zoom,
        maxZoom: 12,
        minZoom: 1,
        antialias: true
      }));

      map.value.on('load', () => {
        map.value.addSource('europa', {type: 'geojson', data: 'components/assets/countries.geojson'});
        map.value.addLayer({
            'id': 'europa',
            'type': 'fill',
            'source': 'europa',
            'layout': {},
            'paint': {
                'fill-antialias': true,
                'fill-color': '#111',
                'fill-opacity': 1.0,
                'fill-outline-color': '#888'
            }
        });

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
@import '/maplibre-gl.css';

.map-wrap {
  position: relative;
  width: 98%;
  height: calc(100vh - 500px); /* calculate height of the screen minus the heading */
}

.map {
  position: absolute;
  width: 100%;
  height: 100%;
}
</style>
