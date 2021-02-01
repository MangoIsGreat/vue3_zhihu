<template>
  <teleport to='#modal'>
      <div id="center">
          <h2>this is a modal</h2>
      </div>
  </teleport>
</template>

<script lang="ts">
export default {

}
</script>

<style>
#center {
    width: 200px;
    height: 200px;
    border: 2px solid black;
    background-color: #fff;
    position: fixed;
    left: 50%;
}
</style>