<template>
    <div>
        <h2>Рандомные числа</h2>
        <div class="box" v-for="(number, index) in numbers" :key="index" @mouseover="changeSize(index)"
            @mouseleave="resetSize(index)">
            {{ number }}
        </div>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            numbers: []
        };
    },
    created() {
        this.generateRandomNumbers();
        setInterval(this.changeRandomNumber, 1000);
    },
    methods: {
        generateRandomNumbers() {
            for (let i = 0; i < 10; i++) {
                this.numbers.push(this.generateRandomNumber());
            }
        },
        generateRandomNumber() {
            return Math.floor(Math.random() * 100);
        },
        changeRandomNumber() {
            const indexToChange = Math.floor(Math.random() * 10);
            this.numbers[indexToChange] = this.generateRandomNumber();
        },
        changeSize(index) {
            this.hoveredIndex = index;
        },
        resetSize() {
            this.hoveredIndex = null;
        }

    }
};
</script>
  
<style scoped>
.box {
    border: 2px solid black;
    border-radius: 10px;
    padding: 10px;
    margin: 10px;
    transition: transform 0.3s ease;
}
.box:hover {
  transform: scale(0.8); 
}
</style>