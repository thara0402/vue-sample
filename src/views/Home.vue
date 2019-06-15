<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
    <p>{{greetText}}</p>
    <p>ご注文回数：{{count}}回</p>
    <p v-if="isRegulars">ありがとうございます。</p>
    <p>
      <MyButton :greet="greetText" @clicked="onMyButtonClicked">ぴょんぴょん</MyButton>
    </p>
    <p>
      <ResetButton v-model="greetText">もう１回！</ResetButton>
    </p>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch } from 'vue-property-decorator';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
import MyButton from "@/components/MyButton.vue";
import ResetButton from "@/components/ResetButton.vue";

@Component({
  components: {
    HelloWorld,
    MyButton,
    ResetButton,
  },
})
export default class Home extends Vue {
  private count: number = 0;
  private greetText: string = "ご注文はうさぎですか？";

  public get isRegulars(): boolean{
    return this.count >= 3;
  }

  @Watch('count')
  public countChanged(){
    if (this.count == 3){
      alert("もふもふ");
    }
  }

  public onMyButtonClicked(count: number){
    this.count = count;
    this.greetText = "ご注文はうさぎですか？？";
  }
}
</script>
