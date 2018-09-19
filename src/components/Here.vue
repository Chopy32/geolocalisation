<template>
    <div id="map"></div>
</template>

<script>
    export default {
        name: "Here",
        mounted : function () {
            var platform = new H.service.Platform({
                'app_id': 'nXoqqsGScgvXbxl6eBmR',
                'app_code': 'HaMgrGypT5AHTMc-f6oQIQ'
            });

            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(function (position) {

                    var lon = position.coords.longitude
                    var lat = position.coords.latitude

                    var maptypes = platform.createDefaultLayers();

                    // Instantiate (and display) a map object:
                    var map = new H.Map(
                        document.getElementById('map'),
                        maptypes.normal.map,
                        {
                            zoom: 15,
                            center: { lng: lon, lat: lat }
                        });

                });
            } else {
                alert("Activez la géolocalisation sur votre navigateur")
            }



        }
    }
</script>

<style scoped>
    #map {
        height: 100%;
        width: 100%;
    }
</style>