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
    #map h1 {
        text-align: center;
    }
    #map header {
        background-color: pink;
        padding: 20px;
    }

    #map footer {
        background-color: grey;
        padding:20px;
        text-align: center;
    }

    #map .main_body {
        height: 800px;
    }

    #map {
        height: 100%;
        width: 100%;
    }

    #map img {
        width: 100%;
        height: 100%;
    }

</style>