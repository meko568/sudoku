<template>
  <div class="game">
    <div class="game-area">
      <div class="mistakes-counter">
        <p>Mistakes: <span>0</span>/3</p>
      </div>
      <div class="row mainrow">
        <div class="therow col-4 row">
          <div class="block row1 cube1 column1 col-4"></div>
          <div class="block row1 cube1 column2 col-4"></div>
          <div class="block row1 cube1 column3 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row1 cube2 column4 col-4"></div>
          <div class="block row1 cube2 column5 col-4"></div>
          <div class="block row1 cube2 column6 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row1 cube3 column7 col-4"></div>
          <div class="block row1 cube3 column8 col-4"></div>
          <div class="block row1 cube3 column9 col-4"></div>
        </div>
      </div>
      <div class="row mainrow">
        <div class="therow col-4 row">
          <div class="block row2 cube1 column1 col-4"></div>
          <div class="block row2 cube1 column2 col-4"></div>
          <div class="block row2 cube1 column3 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row2 cube2 column4 col-4"></div>
          <div class="block row2 cube2 column5 col-4"></div>
          <div class="block row2 cube2 column6 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row2 cube3 column7 col-4"></div>
          <div class="block row2 cube3 column8 col-4"></div>
          <div class="block row2 cube3 column9 col-4"></div>
        </div>
      </div>
      <div class="row mainrow">
        <div class="therow col-4 row">
          <div class="block row3 cube1 column1 col-4"></div>
          <div class="block row3 cube1 column2 col-4"></div>
          <div class="block row3 cube1 column3 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row3 cube2 column4 col-4"></div>
          <div class="block row3 cube2 column5 col-4"></div>
          <div class="block row3 cube2 column6 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row3 cube3 column7 col-4"></div>
          <div class="block row3 cube3 column8 col-4"></div>
          <div class="block row3 cube3 column9 col-4"></div>
        </div>
      </div>
      <div class="row mainrow">
        <div class="therow col-4 row">
          <div class="block row4 cube4 column1 col-4"></div>
          <div class="block row4 cube4 column2 col-4"></div>
          <div class="block row4 cube4 column3 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row4 cube5 column4 col-4"></div>
          <div class="block row4 cube5 column5 col-4"></div>
          <div class="block row4 cube5 column6 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row4 cube6 column7 col-4"></div>
          <div class="block row4 cube6 column8 col-4"></div>
          <div class="block row4 cube6 column9 col-4"></div>
        </div>
      </div>
      <div class="row mainrow">
        <div class="therow col-4 row">
          <div class="block row5 cube4 column1 col-4"></div>
          <div class="block row5 cube4 column2 col-4"></div>
          <div class="block row5 cube4 column3 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row5 cube5 column4 col-4"></div>
          <div class="block row5 cube5 column5 col-4"></div>
          <div class="block row5 cube5 column6 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row5 cube6 column7 col-4"></div>
          <div class="block row5 cube6 column8 col-4"></div>
          <div class="block row5 cube6 column9 col-4"></div>
        </div>
      </div>
      <div class="row mainrow">
        <div class="therow col-4 row">
          <div class="block row6 cube4 column1 col-4"></div>
          <div class="block row6 cube4 column2 col-4"></div>
          <div class="block row6 cube4 column3 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row6 cube5 column4 col-4"></div>
          <div class="block row6 cube5 column5 col-4"></div>
          <div class="block row6 cube5 column6 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row6 cube6 column7 col-4"></div>
          <div class="block row6 cube6 column8 col-4"></div>
          <div class="block row6 cube6 column9 col-4"></div>
        </div>
      </div>
      <div class="row mainrow">
        <div class="therow col-4 row">
          <div class="block row7 cube7 column1 col-4"></div>
          <div class="block row7 cube7 column2 col-4"></div>
          <div class="block row7 cube7 column3 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row7 cube8 column4 col-4"></div>
          <div class="block row7 cube8 column5 col-4"></div>
          <div class="block row7 cube8 column6 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row7 cube9 column7 col-4"></div>
          <div class="block row7 cube9 column8 col-4"></div>
          <div class="block row7 cube9 column9 col-4"></div>
        </div>
      </div>
      <div class="row mainrow">
        <div class="therow col-4 row">
          <div class="block row8 cube7 column1 col-4"></div>
          <div class="block row8 cube7 column2 col-4"></div>
          <div class="block row8 cube7 column3 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row8 cube8 column4 col-4"></div>
          <div class="block row8 cube8 column5 col-4"></div>
          <div class="block row8 cube8 column6 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row8 cube9 column7 col-4"></div>
          <div class="block row8 cube9 column8 col-4"></div>
          <div class="block row8 cube9 column9 col-4"></div>
        </div>
      </div>
      <div class="row mainrow">
        <div class="therow col-4 row">
          <div class="block row9 cube7 column1 col-4"></div>
          <div class="block row9 cube7 column2 col-4"></div>
          <div class="block row9 cube7 column3 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row9 cube8 column4 col-4"></div>
          <div class="block row9 cube8 column5 col-4"></div>
          <div class="block row9 cube8 column6 col-4"></div>
        </div>
        <div class="therow col-4 row">
          <div class="block row9 cube9 column7 col-4"></div>
          <div class="block row9 cube9 column8 col-4"></div>
          <div class="block row9 cube9 column9 col-4"></div>
        </div>
      </div>
      <div class="number-buttons">
        <button class="number-button">1</button>
        <button class="number-button">2</button>
        <button class="number-button">3</button>
        <button class="number-button">4</button>
        <button class="number-button">5</button>
        <button class="number-button">6</button>
        <button class="number-button">7</button>
        <button class="number-button">8</button>
        <button class="number-button">9</button>
        <button class="number-button eraser-button">
          <i class="fas fa-eraser"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "gamePage",
  data() {
    return {
      selectedNumber: null,
      selectedBlock: null,
      gameStarted: false,
      time: "00:00",
      score: 100,
      timer: null,
    };
  },
};
</script>
