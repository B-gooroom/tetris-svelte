<!-- TODO: 'spaceBar'로 끝까지 내리고, 고정, 다음블럭 부르기(랜덤?)
TODO: 블럭들 transform
TODO: x 한줄이 다 차면 없애기(한줄 out) - score +10
TODO: timer 1000 - blocks y + 1 (한줄씩 내려오기) -->

<script>
import { onDestroy } from 'svelte';

const blocks = [
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
  [false, false, false, false, false, false, false, false, false, false],
];
let O = [{x: 4, y: 0}, {x: 5, y: 0}, {x: 4, y: 1}, {x: 5, y: 1}];
let I = [{x: 4, y: 0}, {x: 4, y: 1}, {x: 4, y: 2}, {x: 4, y: 3}];
let T = [{x: 4, y: 0}, {x: 5, y: 0}, {x: 6, y: 0}, {x: 5, y: 1}];
let J = [{x: 5, y: 0}, {x: 5, y: 1}, {x: 5, y: 2}, {x: 4, y: 2}];
let L = [{x: 4, y: 0}, {x: 4, y: 1}, {x: 4, y: 2}, {x: 5, y: 2}];
let Z = [{x: 4, y: 0}, {x: 5, y: 0}, {x: 5, y: 1}, {x: 6, y: 1}];
let S = [{x: 4, y: 0}, {x: 4, y: 1}, {x: 5, y: 1}, {x: 5, y: 2}];

const keyEvent = (event) => {
  console.log(event);
  switch (event.key) {
    case "ArrowLeft":
      if (O[0].x === 0) return;
      for (let index = 0; index < O.length; index++) {
        const child = O[index];
        child.x -= 1;
      }
      O = [...O];
      break;
    case "ArrowRight":
      if (O[0].x === 8) return;
      for (let index = 0; index < O.length; index++) {
        const child = O[index];
        child.x += 1;
      }
      O = [...O];
      console.log("arrowRight");
      break;
    case "ArrowDown":
      if (O[0].y === 19) return;
      for (let index = 0; index < O.length; index++) {
        const child = O[index];
        child.y += 1;
      }
      O = [...O];
      console.log("ArrowDown");
      break;
      // TODO: 모양바꾸기(블럭)
      // case "ArrowUp":
      // if (O[0].y === 19) return;
      // for (let index = 0; index < O.length; index++) {
      //   const child = O[index];
      //   child.y += 1;
      // }
      // O = [...O];
      // console.log("ArrowUp");
      // break;
    default:
      break;
  }
};
$: checkGrid = (x, y) => {
  let isFill = false;
  for (let index = 0; index < O.length; index++) {
    const child = O[index]; 
    if (child.x === x && child.y === y) {
      isFill = true;
      break;
    }
  }
  return isFill ? 'fill' : 'empty';
}

document.addEventListener('keydown', keyEvent);

onDestroy(() => document.removeEventListener('keydown', keyEvent));
</script>

<h3>Play Tetris!</h3>
<div class="board-wrapper">
  <table class="play-board">
    <tbody>
      {#each blocks as gridY, y}
        <tr>
          <td class="extra" />
          {#each gridY as gridX, x}
            <td class={checkGrid(x, y)}>
            </td>
          {/each}
          <td class="extra" />
        </tr>
      {/each}
    </tbody>
  </table>
  <div class="info-board">
    <div class="level">LEVEL
      <div class="detail">1</div>
    </div>
    <div class="level">SCORE
      <div class="detail">0</div>
    </div>
    <div class="level">NEXT
      <div class="detail">??</div>
    </div>
    <div class="level">HELP
      <div class="detail">to be..</div>
    </div>
  </div>
</div>

<style global lang="scss"></style>
