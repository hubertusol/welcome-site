<template>
  <table>
    <tr>
        <th><a href="https://www.youtube.com" target="_blank"><div class="box"><img src="/nw/buttons/yt.png" class="inside"/></div></a></th>
        <th><a href="https://www.netflix.com" target="_blank"><div class="box"><img src="/nw/buttons/netlfix.png" class="inside" style="height: 12vh; width: 12vh;"/></div></a></th>
        <th><div class="box"><a href="https://mail.google.com/mail/u/0/?hl=pl#inbox" target="_blank"><img src="/nw/buttons/gmail.png" class="inside"/></a></div></th>
        <th><div class="box"><a href="https://leetify.com/" target="_blank"><img src="/nw/buttons/csgo.png" class="inside"/></a></div></th>
    </tr>
    <tr>
        <th><a href="https://www.twitter.com" target="_blank" class="behave"><div class="box"><img src="/nw/buttons/tw.png" class="inside"/></div></a></th>
        <th><div class="box"><a href="https://binance.com/pl" target="_blank"><img src="/nw/buttons/binance.png" class="inside"/></a></div></th>
        <th><div class="box"><a href="https://portal.wsb.pl/group/wroclaw" target="_blank"><img src="/nw/buttons/vulcan.png" class="inside"/></a></div></th>
        <th><div class="box"><a href="https://onedrive.live.com/edit.aspx?resid=B235354E4F498A86!720&ithint=file%2cxlsx&wdOrigin=OFFICECOM-WEB.MAIN.EDGEWORTH" target="_blank"><img src="/nw/buttons/gym.png" class="inside"/></a></div></th>
    </tr>
    <tr>
        <th><div class="box"><a href="https://music.youtube.com/" target="_blank"><img src="/nw/buttons/music.png" class="inside"/></a></div></th>
        <th><div class="box"><a href="https://www.messenger.com/" target="_blank"><img src="/nw/buttons/mess.png" class="inside"/></a></div></th>
        <th><div class="box"><a href="https://www.tradingview.com/" target="_blank"><img src="/nw/buttons/btc.png" class="inside"/></a></div></th>
        <th><div class="box"><a href="#" target="_blank"><img src="/nw/buttons/x.png" class="inside"/></a></div></th>
    </tr>
    <tr>
        <th><div class="box"><a href="https://coinmarketcap.com" target="_blank"><img src="/nw/buttons/cmp.png" class="inside"/></a></div></th>
        <th><div class="box"><a href="https://facebook.com" target="_blank"><img src="/nw/buttons/facebook.png" class="inside"/></a></div></th>
        <th><div class="box"><a href="https://github.com/" target="_blank"><img src="/nw/buttons/git.png" class="inside"/></a></div></th>
        <th><div class="box"><a href="#" target="_blank"><img src="/nw/buttons/x.png" class="inside"/></a></div></th>
    </tr>
  </table>
</template>

<script>
export default {

}
</script>

<style>
.box {
  position: relative;
  font-weight: bold;
  line-height: 17vh;
  text-align: center;
  border-radius: 15px;
  margin: auto;
  width: 17vh;
  height: 17vh;
  border: solid 1px white;
  background: linear-gradient(90deg, rgba(219,9,9,0) 0%, rgba(70,74,252,0.5) 100%);
  transition: all 0.5s;
  font-size: 3vh;
}
a , a:visited {
  
  width: 13vh;
  height: 13vh;
  padding: 0;
  margin: 0;
  color: white;
  text-decoration: none;
}
.box:hover {
  font-size: 4vh;
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
.inside {
  opacity:0.6;
  filter:invert(100%);
  width: 14vh;
  height: 14vh;
  margin: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}
@media only screen and (max-width: 1200px) {
  .box {
    height: 13vh;
    width: 13vh;
  }
  .box:hover {
    height: 15vh;
    width: 15vh;
  }
  .inside {
    height: 11vh;
    width: 11vh
  }
}
</style>