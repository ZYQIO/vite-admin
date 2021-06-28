<template>
  <h1>{{ msg }}</h1>
  <p>{{ $store.state.counter }}</p>

  <!-- 国际化 -->
  <form>
    <label>{{ t('language') }}</label>
    <select v-model="locale">
      <option value="en">en</option>
      <option value="ja">ja</option>
    </select>
  </form>
  <p>{{ t('hello') }}</p>

  <el-button @click="state.count++">count is: {{ state.count }}</el-button>
  <p>
    Edit
    <code>components/HelloWorld.vue</code> to test hot module replacement.
  </p>

  <p>--------------------------------------------------------------------------------</p>


  <!-- <h1>foreach map遍历时怎么中途退出循环</h1> -->
  

</template>

<script setup>
import { defineProps, reactive, onMounted } from "vue";
import { useI18n } from "vue-i18n";

defineProps({
  msg: String,
});

const state = reactive({ count: 0 });
const { locale, t } = useI18n({
  inheritLocale: true,
});

onMounted(() => {
  console.log(111);

  function Texxt (params) {
    // this.state = {id: 1}
    
    console.log('arguments', Array.from(arguments));

  }

  // const p = new Texxt()

  console.log('Texxt', Texxt(1,2,3,4,5));

  let array = [
    {id: 1, msg:'傲娇地方拉三等奖'},
    {id: 2, msg:'123546465'},
    {id: 3, msg:'agsdfgsdfg'}
  ]

  array.forEach(item => {
    if (item.id === 2) {
      return
    }
    console.log(item.msg);
  })

})


</script>

<i18n>
{
  "en": {
    "language": "Language",
    "hello": "hello, world!"
  },
  "ja": {
    "language": "言語",
    "hello": "こんにちは、世界！"
  }
}
</i18n>

<style scoped>
a {
  color: #42b983;
}
</style>
