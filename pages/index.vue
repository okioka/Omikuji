<template>
  <section class="section">
    <div class="columns is-mobile">
      <h1 class="column title" style="color:gray">おみくじ</h1>
      <button class="button is-primary" @click="lottery()">
        <strong class="has-text-white">抽選</strong>
      </button>
    </div>

    <div v-if="isLottery">
    <h2>結果</h2>
    <div class="card mt-3 pb-3" v-for="result in results" :key="result.id">
      <div class="content p-4">
        <p class="title">運勢 : {{ result.fortune }}</p>
        <p>願事 : {{ result.wish }}</p>
        <p>恋愛 : {{ result.love }}</p>
        <p>仕事 : {{ result.business }}</p>
        <p>待人 : {{ result.waiter }}</p>
      </div>
    </div>
  </div>

  </section>
</template>

<script>
  export default {
    data(){
      return {
        results: [],
        isLottery: false
      }
    },
    methods: {
      lottery() {
        this.results.unshift({
          'id': this.results.length,
          'fortune': this.fortune_lottery(), //運勢
          'wish': this.others_lottery(), //願事
          'love': this.others_lottery(), //恋愛
          'business': this.others_lottery(), // 仕事
          'waiter': this.others_lottery(), // 待人
        })
        this.isLottery = true
      },
      // 運勢抽選
      fortune_lottery() {
        const result = Math.round( Math.random()*100 ) % 6;
        switch(result) {
          case 0:  return "大吉";
          case 1:  return "中吉";
          case 2:  return "小吉";
          case 3:  return "吉";
          case 4:  return "凶";
          case 5:  return "大凶"
          default: return "抽選失敗";
        }
      },
      // その他抽選
      others_lottery() {
        const result = Math.round( Math.random()*100 ) % 2;
        switch(result) {
          case 0:  return "良";
          case 1:  return "悪";
          default: return "抽選失敗";
        }
      }
    }
  }
</script>
