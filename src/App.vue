<template>
    <div class="container">
        <google-map></google-map>
    </div>
</template>

<script>
    import GoogleMap from './components/GoogleMap'


    export default {
        name: 'app',
        data() {
            return {
            }
        },
        components : {
            GoogleMap
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
    }

</style>
