<template>
  <div class="home">
    <h1>sudoku game</h1>
    <div class="select-game">
      <h3>game ranks</h3>
      <div>
        <div class="easy text-capitalize">
          <router-link to="/game" class="text-capitalize nav-link new"
            >easy</router-link
          >
        </div>
        <div class="medium text-capitalize">
          <router-link to="/game" class="text-capitalize nav-link new"
            >medium</router-link
          >
        </div>
        <div class="hard text-capitalize">
          <router-link to="/game" class="text-capitalize nav-link new"
            >hard</router-link
          >
        </div>
        <div class="expert text-capitalize">
          <router-link to="/game" class="text-capitalize nav-link new"
            >expert</router-link
          >
        </div>
      </div>
    </div>
    <router-view />
  </div>
</template>

<script>
// @ is an alias to /src
import "@/assets/game.js";
export default {
  name: "HomeView",
  data: function () {
    return {
      mistakes: 0,
      maxMistakes: 3,
      gameStarted: false,
      time: "00:00",
      score: 0,
      timer: null,
      row1: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      row2: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      row3: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      row4: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      row5: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      row6: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      row7: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      row8: [1, 2, 3, 4, 5, 6, 7, 8, 9],
      row9: [1, 2, 3, 4, 5, 6, 7, 8, 9],
    };
  },
  mounted() {
    this.work();
  },
  methods: {
    work: function () {
      this.ex();
      let games = document.querySelectorAll(".new");
      games.forEach((game) => {
        game.onclick = () => {
          // Set difficulty level
          let difficulty = 0;
          if (game.innerHTML === "easy") {
            difficulty = 6;
          }
          if (game.innerHTML === "medium") {
            difficulty = 5;
          }
          if (game.innerHTML === "hard") {
            difficulty = 4;
          }
          if (game.innerHTML === "expert") {
            difficulty = 3;
          }
          // Initialize game
          let rows = document.querySelectorAll(".mainrow");
          let grid = this.ex();
          let index1 = 0;

          // Randomly select 3 blocks from each 3x3 cube
          const randomBlocks = new Set();

          // There are 9 cubes (3x3 subgrids) in Sudoku
          for (let cubeRow = 0; cubeRow < 3; cubeRow++) {
            for (let cubeCol = 0; cubeCol < 3; cubeCol++) {
              // Select 3 random blocks from this cube
              const cubeBlocks = [];
              for (let row = 0; row < 3; row++) {
                for (let col = 0; col < 3; col++) {
                  // Calculate global index for this block
                  const globalIndex =
                    cubeRow * 27 + cubeCol * 3 + row * 9 + col;
                  cubeBlocks.push(globalIndex);
                }
              }

              // Shuffle the blocks in this cube and take 3
              cubeBlocks.sort(() => Math.random() - 0.5);
              for (let i = 0; i < difficulty; i++) {
                randomBlocks.add(cubeBlocks[i]);
              }
            }
          }

          rows.forEach(function (e) {
            let three = Array.from(e.children);
            let blocks = [];
            three.forEach(function (t) {
              blocks.push(...t.children);
            });

            let row = grid[index1];
            let index2 = 0;

            blocks.forEach(function (b) {
              const num = row[index2];
              b.dataset.num = num;

              // Calculate the unique index for this block (0-80)
              const blockIndex = index1 * 9 + index2;

              // If this block is in our random selection, show its number
              if (randomBlocks.has(blockIndex)) {
                b.innerHTML = num;
              }

              index2++;
            });
            index1++;
          });
          this.checkgame();
        };
      });
    },
    checkgame: function () {
      let blocks = document.querySelectorAll(".block");
      let vm = this;
      let finish = 0;
      let earserButton = document.querySelector(".eraser-button");
      let group1 = null;
      let group2 = null;
      let group3 = null;
      let controls = document.querySelectorAll(
        ".number-button:not(.eraser-button)"
      );
      blocks.forEach((block) => {
        block.onclick = function () {
          blocks.forEach((b) => {
            b.classList.remove("selected-block");
          });
          blocks.forEach((e) => {
            if (e.innerHTML === block.innerHTML && e.innerHTML !== "") {
              e.classList.add("correct");
            } else {
              e.classList.remove("correct");
            }
          });
          this.classList.add("selected-block");
        };
        group1 = document.querySelectorAll(`.${block.classList[1]}`);
        group2 = document.querySelectorAll(`.${block.classList[2]}`);
        group3 = document.querySelectorAll(`.${block.classList[3]}`);
      });
      controls.forEach((control) => {
        control.onclick = function () {
          if (document.querySelector(".selected-block")) {
            let block = document.querySelector(".selected-block");
            let num = this.innerHTML;
            block.innerHTML = num;
            group1 = document.querySelectorAll(`.${block.classList[1]}`);
            group2 = document.querySelectorAll(`.${block.classList[2]}`);
            group3 = document.querySelectorAll(`.${block.classList[3]}`);
            if (block.innerHTML !== block.dataset.num) {
              vm.mistakes++;
              document.querySelector("p span").innerHTML =
                +document.querySelector("p span").innerHTML + 1;
              if (vm.mistakes === vm.maxMistakes) {
                alert("game-over");
              }
              block.classList.add("wrong");
              group1.forEach((b) => {
                if (b.innerHTML === block.innerHTML) {
                  b.classList.add("wrong");
                } else {
                  b.classList.remove("wrong");
                }
              });
              group2.forEach((b) => {
                if (b.innerHTML === block.innerHTML) {
                  b.classList.add("wrong");
                } else {
                  b.classList.remove("wrong");
                }
              });
              group3.forEach((b) => {
                if (b.innerHTML === block.innerHTML) {
                  b.classList.add("wrong");
                } else {
                  b.classList.remove("wrong");
                }
              });
            } else {
              blocks.forEach((e) => {
                if (e.innerHTML === block.innerHTML && e.innerHTML !== "") {
                  e.classList.add("correct");
                } else {
                  e.classList.remove("correct");
                }
              });
              group1.forEach((b) => {
                b.classList.remove("wrong");
              });
              group2.forEach((b) => {
                b.classList.remove("wrong");
              });
              group3.forEach((b) => {
                b.classList.remove("wrong");
              });
              finish = Array.from(blocks).filter(
                (block) => block.innerHTML === block.dataset.num
              ).length;
              let full1 = Array.from(group1).filter(
                (e) => e.innerHTML === e.dataset.num
              );
              if (full1.length === 9) {
                block.parentElement.parentElement.classList.add("full");
                setTimeout(() => {
                  block.parentElement.parentElement.classList.add("none");
                }, 700);
              }
              if (finish === blocks.length) {
                alert("game over");
              }
            }
          }
        };
        earserButton.onclick = function () {
          document.querySelector(".selected-block").innerHTML = "";
          blocks.forEach((e) => {
            e.classList.remove("correct");
            e.classList.remove("wrong");
          });
        };
      });
    },
    ex: function () {
      function generateRandomSudoku() {
        // Create a 9x9 grid filled with zeros
        const grid = Array(9)
          .fill()
          .map(() => Array(9).fill(0));

        // Helper function to check if a number can be placed
        function isValid(y, x, num) {
          // Check row
          for (let i = 0; i < 9; i++) {
            if (grid[y][i] === num) return false;
          }

          // Check column
          for (let i = 0; i < 9; i++) {
            if (grid[i][x] === num) return false;
          }

          // Check 3x3 box
          const boxRow = Math.floor(y / 3) * 3;
          const boxCol = Math.floor(x / 3) * 3;
          for (let i = 0; i < 3; i++) {
            for (let j = 0; j < 3; j++) {
              if (grid[boxRow + i][boxCol + j] === num) return false;
            }
          }

          return true;
        }

        // Helper function to solve the grid
        function solve(y = 0, x = 0) {
          if (y === 9) return true; // Reached end of grid
          if (x === 9) return solve(y + 1, 0); // Move to next row

          if (grid[y][x] !== 0) return solve(y, x + 1); // Skip filled cells

          // Try numbers 1-9
          const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];
          numbers.sort(() => Math.random() - 0.5); // Shuffle numbers

          for (const num of numbers) {
            if (isValid(y, x, num)) {
              grid[y][x] = num;
              if (solve(y, x + 1)) return true;
              grid[y][x] = 0; // Backtrack
            }
          }
          return false;
        }

        // Generate a random pattern
        solve();

        return grid;
      }
      return generateRandomSudoku();
    },
  },
};
</script>
