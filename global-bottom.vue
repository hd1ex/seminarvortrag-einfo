<template>
  <footer
    v-if="$slidev.nav.currentLayout !== 'cover'"
    class="absolute bottom-0 left-0 right-0 p-2"
  >
    Folie {{ $slidev.nav.currentPage }} / {{ $slidev.nav.total }}
  </footer>
</template>

