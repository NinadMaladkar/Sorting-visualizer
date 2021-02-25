<template>
  <div class="hello">
    <div class="bars">
      <div class="item-bars" v-for="item in newArr" :key="item" :style="{height: (item)+'px'}"></div>
      <div>
        <button @click="generateNewArray">Generate New Array</button>
        <button @click="bubbleSort">Bubble Sort</button>
        <button @click="SelectionSort">Selection Sort</button>
        <button @click="mergeSort">Merge Sort</button>
        <button @click="quickSort">Quick Sort</button>
      </div>
    </div>
  </div>
</template>

<script>
import Sorting from "../services/methods";
export default {
  name: "HelloWorld",
  data() {
    return {
      newArr: [],
      ANIMATION_SPEED_MS: 20,
      NUMBER_OF_ARRAY_BARS: 30,
      PRIMARY_COLOR: "blue",
      SECONDARY_COLOR: "red"
    };
  },

  created() {
    this.resetArray();
    // render() {
    //   const { newArr } = this.state;
    //   return newArr.map(value => <div className="key-bar"> {value} </div>);
    // }
  },
  methods: {
    generateRandomInt: function(min, max) {
      return Math.floor(Math.random() * (max - min + 1) + min);
    },
    resetArray() {
      this.newArr = [];
      for (let i = 0; i <= this.NUMBER_OF_ARRAY_BARS; i++) {
        this.newArr.push(this.generateRandomInt(5, 700));
      }
    },
    generateNewArray() {
      this.resetArray();
    },
    bubbleSort() {},
    selectionSort() {},
    quickSort() {},

    mergeSort() {
      let animations = Sorting.getMergeSortAnimations(this.newArr);

      for (let i = 0; i < animations.length; i++) {
        const arrayBars = document.getElementsByClassName("item-bars");
        const isColorChange = i % 3 !== 2;
        if (isColorChange) {
          const [barOneIdx, barTwoIdx] = animations[i];
          const barOneStyle = arrayBars[barOneIdx].style;
          const barTwoStyle = arrayBars[barTwoIdx].style;
          const color = i % 3 === 0 ? this.SECONDARY_COLOR : this.PRIMARY_COLOR;
          setTimeout(() => {
            barOneStyle.backgroundColor = color;
            barTwoStyle.backgroundColor = color;
          }, i * this.ANIMATION_SPEED_MS);
        } else {
          setTimeout(() => {
            const [barOneIdx, newHeight] = animations[i];
            const barOneStyle = arrayBars[barOneIdx].style;
            barOneStyle.height = `${newHeight}px`;
          }, i * this.ANIMATION_SPEED_MS);
        }
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.bars {
  position: absolute;
  margin-left: 100px;
}

.item-bars {
  width: 20px;
  background-color: #42b983;
  display: inline-block;
  margin: 0 1px;
}
</style>
