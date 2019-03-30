<template>
    <div class="home">
        <h1>
            Visualizing Sorting <span class="badge badge-info">by Mvtthew</span>
        </h1>
        <div class="card">
            <div class="card-header">
                <p class="m-0">
                    Options
                </p>
            </div>
        </div>
        <bubble-sort :size="size" :speed="speed" class="mt-5"></bubble-sort>
    </div>
</template>

<script>
    import BubbleSort from "../components/BubbleSort";
    export default {
        name: 'home',
        components: {BubbleSort},
        data() {
            return {
                size: 20,
                speed: 100,
            }
        }
    }
</script>
