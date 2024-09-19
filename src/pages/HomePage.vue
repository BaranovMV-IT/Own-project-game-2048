<template>
  <div class="block">
    <div class="block__header">
      <div class="block__header__name">2048</div>
      <div class="block__header__info">
        <div class="block__header__info__item">
          <div class="block__header__info__item__title">СЧЁТ</div>
          <div class="block__header__info__item__result"></div>
        </div>
        <div class="block__header__info__item">
          <div class="block__header__info__item__title">РЕКОРД</div>
          <div class="block__header__info__item__result"></div>
        </div>
      </div>
    </div>
    <div class="block__board">
      <div class="block__board__cell"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
  data(){
    return {

    }
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