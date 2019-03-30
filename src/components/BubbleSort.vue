<template>
    <div class="bubble-sort">
        <div class="card">
            <div class="card-header">
                <div class="row">
                    <div class="col-6">
                        <h2 class="m-0">Bubble sort</h2>
                    </div>
                    <div class="col-6 text-right">
                        <button class="btn btn-outline-dark mr-2" @click="initialize" v-show="!sorting">
                            Randomize
                        </button>
                        <button class="btn btn-info" @click="bubbleSort">
                            Sort
                        </button>
                    </div>
                </div>
            </div>
            <div class="card-body text-center">
                <span v-for="(item, index) in tab"
                      :class="{'text-warning': index === checking, 'text-info': index === actual, 'text-success': item.done}">
                    {{item.value}}
                </span>
            </div>
            <div class="p-4 chart-box">
                <div class="chart">
                    <div class="stick"
                         :class="{'bg-warning': index === checking, 'bg-info': index === actual, 'bg-success': item.done}"
                         :style="{'height': item.value + '%', 'width': 100 / saved.size + '%'}"
                         v-for="(item, index) in tab"></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'bubble-sort',
        props: ['size', 'speed'],
        data() {
            return {
                tab: [{}],
                actual: -1,
                checking: -1,
                sorting: false,
                saved: {
                    size: '',
                    speed: '',
                }
            }
        },
        created() {
            this.initialize();
        },
        updated() {
            if (this.saved.size !== this.size) {
                this.initialize();
            }
        },
        methods: {
            initialize() {
                if (!this.sorting) {
                    let generated = [];
                    for (let i = 0; i < this.size; i++) {
                        generated[i] = {
                            id: i,
                            value: Math.floor(Math.random() * 100),
                            done: false
                        };
                    }
                    this.tab = generated;
                    this.saved.size = this.size;
                    this.saved.speed = this.speed;
                }
            },
            bubbleSort() {
                if (!this.sorting) {
                    this.sorting = true;
                    let time = -(this.saved.speed * this.saved.size);
                    for (let i = 0; i < this.saved.size; i++) {
                        time += (this.saved.speed * (this.saved.size - i));
                        setTimeout(() => {
                            for (let j = 0; j < this.saved.size - i - 1; j++) {
                                setTimeout(() => {
                                    this.checking = j;
                                    this.actual = j + 1;
                                    if (this.tab[j].value > this.tab[j + 1].value) {
                                        const tmp = this.tab[j];
                                        this.$set(this.tab, j, this.tab[j + 1]);
                                        this.$set(this.tab, j + 1, tmp);
                                    }
                                    if (j + 1 === this.saved.size - i - 1) {
                                        this.tab[j + 1].done = true;
                                    }
                                    if (this.saved.size - i === 2) {
                                        this.tab[0].done = true;
                                        this.checking = -1;
                                        this.actual = -1;
                                        this.sorting = false;
                                    }
                                }, j * this.saved.speed);
                            }
                        }, time);
                    }
                }
            },
        }
    }
</script>

<style lang="scss">

</style>