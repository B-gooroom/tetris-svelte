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

<div>
  <h1>Tetris</h1>
  <table class="playBoard">
    <tbody>
      <!-- {tetris.map((gridY, i) => ( -->
      {#each blocks as gridY, i}
        <tr>
          <td class="extra" />
          {#each gridY as gridX, j}
            <td class={gridX ? "fill" : "empty"}>
              {gridX}
            </td>
          {/each}
          <td class="extra" />
        </tr>
      {/each}
    </tbody>
  </table>
</div>
