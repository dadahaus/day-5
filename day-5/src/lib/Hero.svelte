<script>
  const track = document.getElementById("image-track")
window.onmousedown = e => {
  track.dataset.mouseDownAt = e.clientX;
}
window.onmouseup = e => {
  
  track.dataset.mouseDownAt = "0";
}

window.onmousemove = e => {
  if(track.dataset.mouseDownAt === "0") return;
  const mouseDelta = parseFloat(track.dataset.mouseDownAt) - e.clientX,
  maxDelta = window.innerWidth / 2;

  const percentage = (mouseDelta / maxDelta) * -100;
  track.style.transform = `translate(${percentage}%, -50%)`
}
console.log(track)

</script>

<section>
  <div id="image-track" data-mouse-down-at="0">
    <img class="image" src="src/assets/1.png" alt="" draggable="false"/>
    <img class="image" src="src/assets/2.png" alt="" draggable="false"/>
    <img class="image" src="src/assets/3.png" alt="" draggable="false"/>
    <img class="image" src="src/assets/4.png" alt="" draggable="false"/>
  </div>
</section>

<style lang="scss">
  #image-track {
    display: flex;
    gap: 4vmin;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(0%, -50%);
    .image {
      width: 40vmin;
      height: 56vmin;
      object-fit: cover;
      object-position: center;
    }
  }
</style>
