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
            <div class="card-body">
                <div class="row">
                    <div class="col-lg-3">
                        <div class="form-group">
                            <label for="size">Size (elements to sort)</label>
                            <input class="form-control" id="size" type="number" v-model="size"/>
                        </div>
                    </div>
                    <div class="col-lg-3">
                        <div class="form-group">
                            <label for="speed">Speed (ms/tick)</label>
                            <input class="form-control" id="speed" type="number" v-model="speed"/>
                        </div>
                    </div>
                </div>

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
                size: 90,
                speed: 20,
            }
        }
    }
</script>
