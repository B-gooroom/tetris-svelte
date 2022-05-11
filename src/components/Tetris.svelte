<script>
  const iBlock = [0, 0];
  const blocks = [
    [false, false, false, false, false, false, false, false, false, false],
    [false, false, false, false, false, false, false, false, false, false],
    [false, false, false, false, false, false, false, false, false, false],
    [false, false, false, false, false, false, false, false, false, false],
    [true, true, false, false, false, false, false, false, false, false],
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
</script>

<h3>Play Tetris!</h3>
<div class="board-wrapper">
  <table class="play-board">
    <tbody>
      {#each blocks as gridY, i}
        <tr>
          <td class="extra" />
          {#each gridY as gridX, j}
            <td class={gridX ? "fill" : "empty"}>
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
