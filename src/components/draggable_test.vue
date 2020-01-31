<template>
  <div>
    <div id=d1 v-drag>
        Drag me 1
    </div>
    <div id=d2 v-drag>
        Drag me 2
    </div>
  </div>
</template>

<script>
import drag from '@branu-jp/v-drag'

export default {
  directives: {
    drag
  }
}
</script>

<style>
#d1{
    width: 400px;
    z-index:1000 ;
    position: fixed;
    top: 50%;
    left: 50%;
    -webkit-transform: translate(-40%,-40%);
    transform: translate(-20%, -40%);
}
#d2{
    width: 400px;
    z-index:1000 ;
    position: fixed;
    top: 50%;
    left: 50%;
    -webkit-transform: translate(-40%,-40%);
    transform: translate(-50%, -40%);
}
</style>