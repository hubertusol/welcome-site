<template>
  <table>
    <tr>
        <th><div class="box">1</div></th>
        <th><div class="box">2</div></th>
        <th><div class="box">3</div></th>
        <th><div class="box">4</div></th>
    </tr>
    <tr>
        <th><div class="box">5</div></th>
        <th><div class="box">6</div></th>
        <th><div class="box">7</div></th>
        <th><div class="box">8</div></th>
    </tr>
    <tr>
        <th><div class="box">9</div></th>
        <th><div class="box">10</div></th>
        <th><div class="box">11</div></th>
        <th><div class="box">12</div></th>
    </tr>
    <tr>
        <th><div class="box">13</div></th>
        <th><div class="box">14</div></th>
        <th><div class="box">15</div></th>
        <th><div class="box">16</div></th>
    </tr>
  </table>
</template>

<script>
export default {

}
</script>

<style>
.box {
  line-height: 17vh;
  text-align: center;
  border-radius: 15px;
  margin: auto;
  width: 17vh;
  height: 17vh;
  border: solid 1px white;
  background: linear-gradient(90deg, rgba(219,9,9,0) 0%, rgba(70,74,252,0.5) 100%);
  transition: all 0.5s;
}
.box:hover {
  line-height: 20vh;
  height: 20vh;
  width: 20vh;
  background: linear-gradient(90deg, rgba(51,9,219,0) 24%, rgba(255,0,0,1) 100%);
  cursor: pointer;
}
th {
  height: 25%;
  width: 25%;
}
</style>