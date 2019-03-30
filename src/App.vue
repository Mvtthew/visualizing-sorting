<template>
    <div id="app">
        <navbar></navbar>
        <div class="container my-4">
            <router-view/>
        </div>
    </div>
</template>

<style lang="scss">

</style>
<script>
    import Navbar from "./components/Navbar";

    export default {
        components: {Navbar}
    }
</script>