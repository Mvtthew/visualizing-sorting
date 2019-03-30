<template>
    <div class="home">
        <h1 class="h3">
            Visualizing Sorting <span class="badge badge-info">by Mvtthew</span>
        </h1>
        <hr>
        <div class="card mt-3">
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
                            <input class="form-control" id="size" type="number" v-model.number="size" min="1" max="5000" required/>
                        </div>
                    </div>
                    <div class="col-lg-3">
                        <div class="form-group">
                            <label for="speed">Speed (ms/tick)</label>
                            <input class="form-control" id="speed" type="number" v-model.number="speed" min="2" max="5000" required/>
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
                size: 30,
                speed: 20,
            }
        },
        updated() {
            if (this.size < 2){
                this.size = 2;
            }
            if (this.speed < 2){
                this.speed = 2;
            }
        }
    }
</script>
