<script setup lang="ts">
import {computed, ref} from "vue";

const inputRef = ref("古古米");
const now = new Date().getFullYear();
const yearAgo = computed(() => {
  return (inputRef.value.match(/古/g) || []).length;
});
const year = computed(() => now - yearAgo.value);

const messages = [
  { message: "ピカピカの新米！炊き立て最高！", year: 1 },
  { message: "まだまだイケる、ちょい古米！", year: 2 },
  { message: "そろそろ味に深みが…？", year: 3 },
  { message: "お米も人生も熟成が大事。", year: 4 },
  { message: "タイムカプセル級の古さ！", year: 5 },
  { message: "伝説の古米、もはや神話。", year: 6 },
  { message: "考古学者が欲しがる貴重な一品！", year: 7 },
  { message: "縄文時代からタイムスリップした米？", year: 8 },
  { message: "恐竜も食べていたかも…？", year: 9 },
  { message: "一粒で十年分の歴史を味わえる！", year: 10 },
  { message: "もはや化石コレクション入り確定！", year: 15 },
  { message: "これは米？それとも歴史的遺物？", year: 20 },
  { message: "博物館に寄贈すべき文化財レベル！", year: 25 },
  { message: "宇宙の始まりを知る古代米！", year: 30 },
  { message: "タイムマシンで過去から持ってきた？", year: 35 },
  { message: "考古学者「新発見です！」", year: 40 },
  { message: "おにぎりにすると時空が歪む！？", year: 45 },
  { message: "これを食べると不老不死になるかも…", year: 50 },
  { message: "ピラミッド建設時に埋められていた！？", year: 55 },
  { message: "アトランティス文明の遺産", year: 60 },
  { message: "このお米、恐竜絶滅の原因説", year: 65 },
  { message: "ビッグバン直後から存在？", year: 70 },
  { message: "パラレルワールドからの来訪者", year: 75 },
  { message: "宇宙人が残していった謎の物体", year: 80 },
  { message: "もはや国宝級！触るのも許可制", year: 85 },
  { message: "時空を超えた古代の叡智", year: 90 },
  { message: "お米の概念を超越した存在", year: 95 },
  { message: "一粒で宇宙の始まりを感じる", year: 100 }
];

const selectedMessage = computed(() => {
  // yearAgoに最も近い年数を持つメッセージを探す
  const sortedMessages = [...messages].sort((a, b) =>
      Math.abs(a.year - yearAgo.value) - Math.abs(b.year - yearAgo.value)
  );
  return sortedMessages[0];
});
</script>

<template>
  <div class="rice-calculator">
    <h1 class="text-5xl font-bold text-center my-16 animate-bounce text-yellow-600">🌾 古米タイムマシン 🌾</h1>
    <h2 class="text-3xl font-bold text-center my-8 bg-gradient-to-r from-amber-500 to-yellow-300 text-transparent bg-clip-text">
      あなたのお米は<span class="text-4xl text-pink-800 animate-pulse">{{year}}年</span>に採れました！
    </h2>
    <div class="message-box p-6 bg-yellow-100 rounded-xl border-4 border-amber-400 shadow-xl max-w-[800px] mx-auto my-8">
      <h3 class="text-2xl text-pink-600 font-bold text-center italic">『{{ selectedMessage.message }}』</h3>
    </div>
    <div class="flex max-w-[1000px] items-center justify-center mx-auto">
      <div class="rice-input-container bg-amber-50 p-6 rounded-2xl shadow-lg">
        <label class="block text-lg text-amber-800 font-bold mb-2">⭐ あなたのお米の状態を教えて ⭐</label>
        <input class="ring-2 ring-amber-400 rounded-2xl p-4 text-xl w-full" v-model="inputRef" placeholder="古古米" />
        <p class="text-sm text-gray-500 mt-2">ヒント：「古」を追加するほど年代が古くなります！</p>
      </div>
    </div>
  </div>
</template>

<style>
@import "tailwindcss";
</style>
