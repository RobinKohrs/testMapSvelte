<script>
  import { onMount } from "svelte";
  import L from "leaflet";

  let container, map;

  onMount(() => {
    map = L.map(container).setView([51.505, -0.09], 13);
    const tiles = L.tileLayer(
      "https://tile.openstreetmap.org/{z}/{x}/{y}.png",
      {
        maxZoom: 19,
        attribution:
          '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
      }
    );
    console.log("tiles: ", tiles);
    tiles.addTo(map);
  });
</script>

<link
  rel="stylesheet"
  href="https://unpkg.com/leaflet@1.9.3/dist/leaflet.css"
  integrity="sha256-kLaT2GOSpHechhsozzB+flnD+zUyjE2LlfWPgU04xyI="
  crossorigin=""
/>

<div id="map" bind:this={container} />

<style>
  #map {
    width: 400px;
    height: 400px;
  }
</style>
