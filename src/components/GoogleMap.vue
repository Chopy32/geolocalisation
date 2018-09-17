<template>
    <div id="map"></div>
</template>

<script>
    export default {
        name: "GoogleMap",
        mounted : function () {
            var platform = new H.service.Platform({
                'app_id': 'nXoqqsGScgvXbxl6eBmR',
                'app_code': 'HaMgrGypT5AHTMc-f6oQIQ'
            });

            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(function (position) {

                    alert(position.coords.longitude+" "+position.coords.latitude)
                    var maptypes = platform.createDefaultLayers();

                    // Instantiate (and display) a map object:
                    var map = new H.Map(
                        document.getElementById('map'),
                        maptypes.normal.map,
                        {
                            zoom: 10,
                            center: { lng: position.coords.longitude, lat: position.coords.latitude }
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