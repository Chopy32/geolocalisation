<template>
    <div>

        <div id="mySidenav" class="sidenav" style="z-index: 100000">
            <div class="w-100" style="height: 200px">
                <a href="javascript:void(0)" class="closebtn" @click="closeNav()">&times;</a>
                <img src="assets/img/map.jpg" class="w-100 h-100">
            </div>
            <a href="javascript:void(0)" :class="'option '+ (view==1?'active':'')" @click="show(1)">Here</a>
            <a href="javascript:void(0)" :class="'option '+ (view==2?'active':'')" @click="show(2)">MapQuest</a>
            <a href="javascript:void(0)" :class="'option '+ (view==3?'active':'')" @click="show(3)">Google map</a>
            <a href="javascript:void(0)" :class="'option '+ (view==4    ?'active':'')" @click="show(4)">Open Street map</a>
        </div>

        <div id="main" class="container-fluid" @click="closeByMain()">
            <header class="row p-2 align-items-center">
                <div class="col-1 col-md-2">
                    <span style="font-size:1rem;cursor:pointer" @click.stop="openNav()">&#9776; <span class="d-md-inline d-none">Menu</span></span>
                </div>
                <h3 class="col-9 col-md-8  pt-1 text-center text">
                    Géolocalisation <i class="fas fa-map-marked"></i>
                </h3>
                <div class="col-1 col-md-2  text-right">
                    <img src="assets/img/icon.png" class="icon" alt="" >
                </div>
            </header>
            <section class="map-container row">
                <here :lat="lat" :lon="lon" v-if="view==1"></here>
                <map-quest :lat="lat" :lon="lon" v-if="view==2"></map-quest>
                <google-map :lat="lat" :lon="lon" v-if="view==3"></google-map>
                <open-street-map :lat="lat" :lon="lon" v-if="view==4"></open-street-map>
            </section>
        </div>

    </div>
</template>

<script>
    import Here from './components/Here'
    import MapQuest from './components/MapQuest'
    import GoogleMap from './components/GoogleMap'
    import OpenStreetMap from './components/OpenStreetMap'

    export default {
        name: 'app',
        data() {
            return {
                view : 0,
                nav : false,

                lon : 0,
                lat : 0
            }
        },
        beforeMount : function() {
            var a = this;

            if (navigator.geolocation){
                navigator.geolocation.getCurrentPosition(
                    function(position) {
                        a.lon = position.coords.longitude;
                        a.lat = position.coords.latitude;
                        a.view =1
                    }
                );
            }else
            {
                alert("Veillez activer la geolocalisation sur votre navigateur");
                a.lat = 3.8480;
                a.lon = 11.5021
            }
        },
        methods : {
            openNav : function () {
                this.nav = true
                document.getElementById("mySidenav").style.width = "250px";
                document.body.style.backgroundColor = "rgba(0,0,0,0.4)";
            },
            closeNav: function () {
                this.nav = false
                document.getElementById("mySidenav").style.width = "0";
                document.body.style.backgroundColor = "white";
            },
            show  :function (view) {
                this.view = view;
                this.closeNav();
            },
            closeByMain:  function () {
                if (this.nav == true)
                    this.closeNav()
            }
        },

        components : {
            Here,
            MapQuest,
            GoogleMap,
            OpenStreetMap

        }
    }

</script>

<style lang="scss">
    @font-face {
        font-family: 'Raleway';
        src: url("/assets/fonts/Raleway-Light.ttf");
    }

    body {
        font-family: 'Raleway', sans-serif;
        font-size: 1rem;
        transition: background-color .5s;
    }

    header {
        border-bottom: 2px solid #6f42c1 ;
        height: 10vh;
        background-color: #fafafa;
    }

    .map-container {
        height: 90vh;
    }

    .text {
        -webkit-animation: text-animation 5s infinite  forwards;
        -o-animation: text-animation 5s infinite forwards;
        animation: text-animation 5s infinite forwards;
        font-size: 1.1rem;

    }

    @keyframes text-animation {
        0% {
            color: #6f42c1;
        }

        50% {
            color: black;
        }

        100% {
            color: #6f42c1;
        }
    }


    .sidenav {
        height: 100%;
        width: 0;
        position: fixed;
        z-index: 1;
        top: 0;
        left: 0;
        background-color: #111;
        overflow-x: hidden;
        transition: 0.5s;
    }

    .sidenav a {
        padding: 8px 8px 8px 32px;
        text-decoration: none;
        font-size: 1rem;
        display: block;
        transition: 0.3s;
        white-space: nowrap;
        color: #f1f1f1;
    }

    .sidenav .option:hover {
        background-color: #6f42c1;
    }


    .active {
        background-color: #6f42c1;
    }

    .sidenav .closebtn {
        color: #6f42c1 ;
        position: absolute;
        top: 0;
        right: 25px;
        font-size: 36px;
        margin-left: 50px;
    }

    #main {
        height: 100vh;
        transition: margin-left .5s;
    }

    .icon {
        width: 1rem;
        height: 1rem;
    }


    @media screen and (max-height: 450px) {
        .sidenav {padding-top: 15px;}
        .sidenav a {font-size: 18px;}
    }

    @media (min-width: 992px) {
        .icon {
            width: 1.2rem;
            height: 1.2rem;
        }

    }

</style>
