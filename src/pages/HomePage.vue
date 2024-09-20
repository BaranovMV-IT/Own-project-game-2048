<template>
  <div class="block">
    <div class="block__header">
      <div class="block__header__name">2048</div>
      <div class="block__header__info">
        <div class="block__header__info__item">
          <div class="block__header__info__item__title">СЧЁТ</div>
          <div class="block__header__info__item__result">{{ score }}</div>
        </div>
        <div class="block__header__info__item">
          <div class="block__header__info__item__title">РЕКОРД</div>
          <div class="block__header__info__item__result">{{ record }}</div>
        </div>
      </div>
    </div>
    <div class="block__board">
      <div class="block__board__cell"
        v-for="cell in Object.keys(cellData)" 
        :key="cell"
        :style="{
          backgroundColor: paintCellByNumber(cellData[cell]),
          color: cellData[cell] == 2 || cellData[cell] == 4 ? 'rgb(119,110,101)' : ''
        }"
      >
        {{ cellData[cell] ? cellData[cell] : "" }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
  data(){
    return {
      cellData: {},
      score: 0,
      record: 0
    }
  },
  methods: {
    fillCellData(){
      let obj = {};

      for(let row=1; row<=4; row++){
        for(let col=1; col<=4; col++){
          const id = row.toString() + col.toString();
          obj[id] = 0;
        }
      }

      this.cellData = obj;
    },
    fillRandomCells(count = 1){
      let obj = {...this.cellData};

      let counter = 0;
      while(counter != count){
        const id = String(Math.floor(Math.random() * (4 - 1 + 1)) + 1) + String(Math.floor(Math.random() * (4 - 1 + 1)) + 1);
          
        if(obj[id] == 0){
          obj[id] = 2;
          counter++
        }
      }

      this.cellData = obj;
    },
    paintCellByNumber(number){
      switch(number){
        case 0:
          return 'rgb(205,193,180)'
        case 2:
          return 'rgb(238,228,218)'
        case 4:
          return 'rgb(237,224,200)'
        case 8:
          return 'rgb(242,177,121)'
        case 16:
          return 'rgb(245,149,99)'
        case 32:
          return 'rgb(246,124,95)'
        case 64:
          return 'rgb(246,94,59)'
        case 128:
          return 'rgb(237,207,114)'
        case 256:
          return 'rgb(237,204,97)'
        case 512:
          return 'rgb(234,199,77)'
        case 1024:
          return 'rgb(236,197,62)'
        case 2048:
          return 'rgb(236,194,49)'
      }
    }
  },
  created(){
    this.fillCellData();
    this.fillRandomCells(2);
  }
}
</script>

<style lang="scss" scoped>
.block {
  display: flex;
  flex-direction: column;
  width: 500px;
  height: fit-content;
  &__header {
    display: flex;
    justify-content: space-between;
    height: 75px;
    margin-bottom: 75px;
    &__name {
      font-size: calc(100% * 5);
      color: rgb(119,110,101);
      font-weight: 700;
      line-height: 1;
    }
    &__info {
      display: flex;
      &__item {
        width: 85px;
        height: fit-content;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 5px 0px;
        background-color: rgb(187,173,160);
        border-radius: 5px;
        margin-left: 10px;
        &__title {
          color: rgb(238,228,218);
        }
        &__result {
          color: rgb(249,246,242);
          font-size: 25px;
          font-weight: 700;
          margin-top: -5px;
        }
      }
    }
  }
  &__board {
    display: flex;
    flex-wrap: wrap;
    width: 100%;
    aspect-ratio: 1/1;
    background-color: rgb(187,173,160);
    border-radius: 5px;
    padding: 20px 0 0 20px;
    &__cell {
      display: flex;
      justify-content: center;
      align-items: center;
      width: calc(100% / 4.7999);
      aspect-ratio: 1/1;
      border-radius: 5px;
      margin: 0 20px 20px 0;
      font-size: calc(100% * 2);
      color: rgb(249,246,242);
      font-family: Verdana, Geneva, Tahoma, sans-serif;
      font-weight: 600;
    }
  }
}
</style>