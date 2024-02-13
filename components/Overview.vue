<template>
  <div>
    <h1 style="margin-bottom: 2em;">Ziele und Gliederung</h1>
    <ol>
      <li :class="{ inactive: isInactive(1) }">Verstehen der Bedeutung des Begriffs <b>Installierte Leistung</b>.</li>
      <li :class="{ inactive: isInactive(2) }">Überblick über den aktuellen <b>Strommix</b>.</li>
      <li :class="{ inactive: isInactive(3) }">Übersicht über den <b>Ausbau</b> der Wind- und Photovoltaikleistung.</li>
      <li :class="{ inactive: isInactive(4) }">Betrachtung des <b>Übertragungsnetzes</b> und dessen geplanter Ausbau.</li>
      <li :class="{ inactive: isInactive(5) }">Spekulation über das geänderte <b>Stromnachfrageverhalten</b> im Jahr 2030.</li>
      <li :class="{ inactive: isInactive(6) }">Analyse potentieller neuer <b>Lastflüsse</b> und Ausblick.</li>
    </ol>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, markRaw } from 'vue';
const props = defineProps(['min', 'max']);
const isInactive = ref((num) => props.min > num || num > props.max);
</script>

<style>
.inactive {
  color: grey;
}
</style>

