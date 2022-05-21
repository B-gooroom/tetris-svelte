<!-- TODO: 고정, 다음블럭 부르기(랜덤?)
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
];
const O = [{x: 4, y: 0}, {x: 5, y: 0}, {x: 4, y: 1}, {x: 5, y: 1}];
const I = [{x: 4, y: 0}, {x: 4, y: 1}, {x: 4, y: 2}, {x: 4, y: 3}];
const T = [{x: 4, y: 0}, {x: 5, y: 0}, {x: 6, y: 0}, {x: 5, y: 1}];
const J = [{x: 5, y: 0}, {x: 5, y: 1}, {x: 5, y: 2}, {x: 4, y: 2}];
const L = [{x: 4, y: 0}, {x: 4, y: 1}, {x: 4, y: 2}, {x: 5, y: 2}];
const Z = [{x: 4, y: 0}, {x: 5, y: 0}, {x: 5, y: 1}, {x: 6, y: 1}];
const S = [{x: 4, y: 0}, {x: 4, y: 1}, {x: 5, y: 1}, {x: 5, y: 2}];

// 블럭을 생성
let currentBlock = JSON.parse(JSON.stringify(O));

const keyEvent = (event) => {
  console.log(event);
  switch (event.key) {
    case "ArrowLeft":
      if (currentBlock[0].x === 0) return;
      for (let index = 0; index < currentBlock.length; index++) {
        const child = currentBlock[index];
        child.x -= 1;
      }
      currentBlock = [...currentBlock];
      break;
    case "ArrowRight":
      if (currentBlock[0].x === 8) return;
      for (let index = 0; index < currentBlock.length; index++) {
        const child = currentBlock[index];
        child.x += 1;
      }
      currentBlock = [...currentBlock];
      console.log("arrowRight");
      break;
    case "ArrowDown":
      if (currentBlock[0].y === 18) return;
      for (let index = 0; index < currentBlock.length; index++) {
        const child = currentBlock[index];
        child.y += 1;
      }
      currentBlock = [...currentBlock];
      console.log("ArrowDown");
      break;
    case " ":
      // 블럭의 마지막 y 값을 찾기위한 = lastY;
      let lastY = 0;
      for (let index = 0; index < currentBlock.length; index++) {
        const child = currentBlock[index];
        if (child.y > lastY) {
          lastY = child.y;
        }
      }
      // child.y = 5 / lastY = 5 /blocks.length = 20
      // 전체 blocks.length 에서 현재 블럭 마지막 위치 lastY 빼주면서 내려갈 child.y 값 계산해줌.
      for (let index = 0; index < currentBlock.length; index++) {
        const child = currentBlock[index];
        child.y += (blocks.length -1) - lastY;
        // blocks에 위치 반영
        blocks[child.y][child.x] = true;
        console.log('nunu', child, blocks[child.y][child.x]);
      }
      currentBlock = JSON.parse(JSON.stringify(I));
      console.log("ArrowDown");
      break;
      // TODO: 모양바꾸기(블럭)
      // case "ArrowUp":
      // if (currentBlock[0].y === 19) return;
      // for (let index = 0; index < O.length; index++) {
      //   const child = currentBlock[index];
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
  for (let index = 0; index < currentBlock.length; index++) {
    const child = currentBlock[index];

    // if (child.x === x && child.y === y) {
    if (
      (child.x === x && child.y === y) // O블럭의 위치 채크
      || (blocks[y][x]) // blocks의 위치도 채크
    ) {
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
