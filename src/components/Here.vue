<template>
    <div class="h-100 w-100 text-center">
        <div class="buttons text-center" style="z-index: 10">
            <button class="btn btn-primary m-2">Zoom +</button>
            <button class="btn btn-danger m-2">Zoom -</button>
        </div>
        <div id="map"></div>
    </div>
</template>

<script>
    export default {
        name: "Here",
        props : {
            lon : 0,
            lat : 0
        },

        data : function() {
            return {
            }
        },

        mounted : function () {
            var platform = new H.service.Platform({
                'app_id': 'nXoqqsGScgvXbxl6eBmR',
                'app_code': 'HaMgrGypT5AHTMc-f6oQIQ'
            });

            var maptypes = platform.createDefaultLayers();

            // Instantiate (and display) a map object:
            var map = new H.Map(
                document.getElementById('map'),
                maptypes.normal.map,
                {
                    zoom: 15,
                    center: { lng:this.lon, lat: this.lat }
                }
            );
        }
    }
</script>

<style scoped>
    #map {
        height: 100%;
        width: 100%;
    }

    .buttons {
        position: absolute;
        bottom: 10px;
        left: 0px;
        right: 0px;
    }
</style>