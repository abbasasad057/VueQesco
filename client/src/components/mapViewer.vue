<template>
    <v-flex id=map>
    </v-flex>
</template>

<script>
import L from 'leaflet';
export default {
    name: 'mapViewer',
    data() {
        return {
            map: null,
            tileLayer: null,
            layers: []
        }
    },
    mounted() {
        this.initMap();
        this.initLayers();
    },
    methods: {
        initMap() {
            this.$store.state.map = L.map('map').setView([30.3753, 69.3451], 5);
            this.tileLayer = L.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token={accessToken}', {
                attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, <a href="https://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
                maxZoom: 18,
                id: 'mapbox/streets-v11',
                accessToken: 'pk.eyJ1IjoiYWJiYXNhc2FkMDU3IiwiYSI6ImNrMWl5Z3BoazA3N2wzaHA1M3J3dDVhdm4ifQ.vr8lXr7BgiEES9ce-s3fkg'
            })
            this.tileLayer.addTo(this.$store.state.map);
        },
        initLayers() {},
}
}
</script>
<style scoped>
#map{
    height: 44.7em !important;
    display: flexbox;
    z-index: -1px!important;
    overflow: hidden;
}
</style>