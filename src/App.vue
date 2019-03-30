<template>
    <div id="app">
        <navbar></navbar>
        <div class="container my-4">
            <router-view/>
        </div>
    </div>
</template>

<script>
    import Navbar from "./components/Navbar";

    export default {
        components: {Navbar}
    }
</script>

<style lang="scss">
    .chart-box{
        position: relative;
        width: 100%;

        .chart{
            width: 100%;
            height: 300px;
            margin-top: auto;
            border: 2px solid rgba(0, 0, 0, 0.1);
            display: flex;
            align-items: end;

            .stick {
                margin-top: auto;
                display: inline-block;
                background-color: black;
            }
        }
    }
</style>