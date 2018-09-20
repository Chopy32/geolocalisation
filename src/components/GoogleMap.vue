<template>
    <div id="map">
        <img src="" id="image">
    </div>
</template>

<script>
    export default {
        name: "GoogleMap",
        props : {
            lon : 0,
            lat : 0
        },
        mounted : function () {
            var img = document.getElementById("image");
            img.src = "https://maps.googleapis.com/maps/api/staticmap?center=" + this.lat + "," + this.lon + "&zoom=15&size=2000x1000&sensor=false";
        }
    }
</script>

<style scoped>
    #map {
        height: 100%;
        width: 100%;
    }

    #map img {
        width: 100%;
        height: 100%;
    }

</style>