<template>
    <div class="bubble-sort">
        <div class="card">
            <div class="card-header">
                <button class="btn btn-primary" @click="bubbleSort">
                    Bubble sort!
                </button>
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
                         :style="{'height': item.value + '%', 'width': 100 / size + '%'}" v-for="(item, index) in tab"></div>
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
            }
        },
        created() {
            for (let i = 0; i < this.size; i++) {
                this.tab[i] = {
                    id: i,
                    value: Math.floor(Math.random() * 100),
                    done: false
                };
            }
        },
        methods: {
            bubbleSort() {
                if (!this.sorting) {
                    this.sorting = true;
                    let time = -(this.speed * this.size);
                    for (let i = 0; i < this.size; i++) {
                        time += (this.speed * (this.size - i));
                        setTimeout( () => {
                            for (let j = 0; j < this.size - i - 1; j++) {
                                setTimeout( () => {
                                    this.checking = j;
                                    this.actual = j + 1;
                                    if (this.tab[j].value > this.tab[j + 1].value) {
                                        const tmp = this.tab[j];
                                        this.$set(this.tab, j, this.tab[j + 1]);
                                        this.$set(this.tab, j + 1, tmp);
                                    }
                                    if (j + 1 === this.size - i - 1) {
                                        this.tab[j + 1].done = true;
                                    }
                                    if (this.size - i === 2) {
                                        this.tab[0].done = true;
                                        this.checking = -1;
                                        this.actual = -1;
                                        this.sorting = false;
                                    }
                                }, j*this.speed);
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