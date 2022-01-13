<template>
  <section class="section">
    <div class="columns is-mobile">
      <h1 class="title" style="color:gray">おみくじ</h1>
    </div>
    <button class="button is-primary" @click="lottery()">
      <strong class="has-text-white">抽選</strong>
    </button>

    // ここで結果を表示する

  </section>
</template>

<script>
  export default {
    data(){
      return {
        result: []
      }
    },
    methods: {
      lottery() {
        this.result.push({
          'fortune': this.fortune_lottery(), //運勢
          'wish': this.others_lottery(), //願事
          'love': this.others_lottery(), //恋愛
          'business': this.others_lottery(), // 仕事
          'waiter': this.others_lottery(), // 待人
        })
      },
      // 運勢抽選
      fortune_lottery() {
        const result = Math.round( Math.random()*100 ) % 6;
        switch(result) {
          case 0: return "大吉";
          case 1: return "中吉";
          case 2: return "小吉";
          case 3: return "吉";
          case 4: return "凶";
          case 5: return "大凶"
        }
      },
      // その他抽選
      others_lottery() {
        const result = Math.round( Math.random()*100 ) % 2;
        switch(result) {
          case 0: return "良";
          case 1: return "悪";
        }
      }
    }
  }
</script>
