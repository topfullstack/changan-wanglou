<template>
  <div id="app" class="p-4">
    <h2>《长安十二时辰》 - 望楼传信系统（二进制版）</h2>
    <h4 class="pt-4 chars">
      <span v-for="(n, i) in chars" :key="n">
        {{n}} {{i}}
      </span>
    </h4>
    <div class="pt-3 d-flex justify-content-center">
      <div class="box"
      v-for="(n, i) in lights"
      :key="i"
      :class="{active: n}"
      @click="$set(lights, i, 1 - n)"
      >
      {{n}}
      </div>
    </div>
    <h3 class="pt-4">
      {{num}} : {{char}}
    </h3>
  </div>
</template>

<script>
export default {
  data(){
    return {
      chars: '张都尉 狼 入 东市 西市 平康 怀远 永宁 皇城'.split(' '),
      lights: Array(4).fill(0)
    }
  },
  computed: {
    num(){
      return parseInt(this.lights.join(''), 2)
    },

    char(){
      return this.chars[this.num]
    }
  }
}
</script>

<style>
body{
  background: #000;
  color: #ecc;
  font-family: "STKaiti";
  text-align: center;
}
.box {
  width: 4rem;
  height: 4rem;
  background: #333;
  margin: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 0.5rem;
}
.box.active{
  background: #ecc;
  color: #333;
}
.chars span {
  display: inline-block;
  width: 2rem;
}
</style>