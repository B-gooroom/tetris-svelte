<script>
  const iBlock = [0, 0];
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
  const O = [{x: 4, y: 0}, {x: 5, y: 0}, {x: 4, y: 1}, {x: 5, y: 1}];
  const I = [{x: 4, y: 0}, {x: 4, y: 1}, {x: 4, y: 2}, {x: 4, y: 3}];
  const T = [{x: 4, y: 0}, {x: 5, y: 0}, {x: 6, y: 0}, {x: 5, y: 1}];
  const J = [{x: 5, y: 0}, {x: 5, y: 1}, {x: 5, y: 2}, {x: 4, y: 2}];
  const L = [{x: 4, y: 0}, {x: 4, y: 1}, {x: 4, y: 2}, {x: 5, y: 2}];
  const Z = [{x: 4, y: 0}, {x: 5, y: 0}, {x: 5, y: 1}, {x: 6, y: 1}];
  const S = [{x: 4, y: 0}, {x: 4, y: 1}, {x: 5, y: 1}, {x: 5, y: 2}];

  const keyEvent = (event) => {
    switch (event.key) {
      case "ArrowLeft":
        // this.directionBar('bar2Direct', -10)
        console.log("arrowLeft");
        break;
      case "ArrowRight":
        // this.directionBar('bar2Direct', 10)
        console.log("arrowRight");
        break;
      default:
        break;
    }
  };
  const checkGrid = (x, y) => {
    let isFill = false;
    for (let index = 0; index < S.length; index++) {
      const child = S[index]; 
      if (child.x === x && child.y === y) {
        isFill = true;
        break;
      }
    }
    return isFill ? 'fill' : 'empty';
  }
</script>

<h3>Play Tetris!</h3>
<div class="board-wrapper">
  <table class="play-board">
    <tbody>
      {#each blocks as gridY, y}
        <tr>
          <td class="extra" />
          {#each gridY as gridX, x}
            <!-- <td class={gridX ? "fill" : "empty"}> -->
            <td class={checkGrid(x, y)}>
              <!-- {gridX} -->
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

<style lang="scss"></style>
