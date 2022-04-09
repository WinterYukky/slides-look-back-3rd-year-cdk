---
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: /aron-visuals-BXOXnQ26B7o-unsplash.jpg
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: true
# persist drawings in exports and build
drawings:
  persist: false
colorSchema: 'dark'
---

# 3年目のCDKを振り返って

Looking back on the 3rd year CDK

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <a href="https://github.com/WinterYukky/slides-look-back-3rd-year-cdk" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# 前回の資料

<div class="grid grid-cols-2 h-4/5 items-center">
  <div>
    <ul>
      <li>Cfn RUMの問題をCDKで解決</li>
      <li>RUM L2を作成してチーム内で利用</li>
      <li>RUM L2のRFCを提出</li>
    </ul>
  </div>
  <div>
    <a href="https://winteryukky.github.io/slides-acceralation-frontend-monitoring-by-awscdk" target="_brank">
      <img src="/prev-title-slide.png" class="rounded-lg" />
    </a>
  </div>
</div>

<!-- 
前回の資料について軽くご紹介しておきます。
前回はCloudFormationにおけるCloudWatch RUMの問題をCDKで解決するストーリーで登壇しました。
L2コンストラクトを作成してチーム内で共有しRUMの導入速度を改善するといった内容です。
現在はRFCとしてレビューしていただいている途中です。
 -->

---
layout: center
class: text-center 
---

前回は少し踏み込んだ内容だったので
<h1>今回は<span class="text-4xl px-2 text-amber-500">ライトな</span>資料に</h1>
<div class="opacity-60">当たり前な内容が多いですが、ご了承ください</div>

<!-- 
当たり前だと思っていることを当たり前だと思わず話す
運用して良かったことや、実際の運用・始める人へおすすめの運用を話す 
-->

---

<the-agenda />

---
layout: intro
---

# 自己紹介

<div class="flex opacity-90">
  <div class="basis-1/4">
    <img src="/profile.png" class="rounded-full h-40 w-40 mx-auto"/>
    <div class="py-3 text-center">
      <div class="text-4xl font-bold">吉川 幸弘</div>
      <div class="pt-1 text-2xl opacity-80">@WinterYukky</div>
    </div>
    <div class="flex justify-around px-5">
      <a href="https://github.com/WinterYukky" target="_blank" alt="GitHub" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
        <mdi-github class="text-3xl" />
      </a>
      <a href="https://twitter.com/WinterYukky" target="_blank" alt="Twitter" class="text-xl icon-btn opacity-50 !border-none !hover:text-sky-500">
        <mdi-twitter class="text-3xl text-sky-500" />
      </a>
    </div>
  </div>
  <div class="basis-3/4 pl-10">
    <ul class="text-2xl">
      <li>通称「ゆっきー」</li>
      <li>大阪のスタートアップ所属エンジニア</li>
      <li>普段のお仕事
        <ul class="text-xl">
          <li>お客様のAWS導入サポート</li>
          <li>プロダクト企画・開発・営業</li>
        </ul>
      </li>
      <li>好きなテクノロジー
        <ul class="text-xl">
          <li>静的型付け言語</li>
          <li>Infrastructure as Code (特にAWS CDK💖)</li>
        </ul>
      </li>
    </ul>
  </div>
</div>

---

<the-agenda :step="1" />

---

# CDKを始めた時の私

<div class="grid grid-cols-5 items-center h-4/5 ">
  <div class="col-span-3 bg-gray-800 z-1 rounded p-6">
    <ul class="opacity-90">
      <li><strong class="text-rose-400">AWS</strong>利用経験なし</li>
      <li><strong class="text-sky-400">TypeScript</strong> チョットデキル</li>
      <li><strong class="text-yellow-400">GKE</strong> チョットデキル</li>
    </ul>
  </div>
  <div class="col-span-2 text-8xl text-center">🐣</div>
</div>
<the-random-falls
  v-if="$slidev.nav.currentPage === 7"
  :speed="100"
  :max="50" 
  :interval="400"
  class="text-6xl opacity-5" 
>🐣</the-random-falls>

---
layout: center
class: text-center
---

# DWHのデータを活用したBIツール
を作成することに

---
layout: center
class: text-center
clicks: 1
---

<h1 :class="{ 'text-dot': $slidev.nav.clicks >= 1 }">過去の話なので雰囲気を変更</h1>

---
layout: center
class: text-center text-dot
---

# DWHのデータを活用したBIツール
を作成することに

---

<h1 class="text-dot">チームメンバーのジョブを決めてください</h1>
<div class="grid grid-cols-3 px-8 text-dot">
  <div class="p-4">
    <div class="flex justify-center items-center">
      <mdi-account class="rounded-full h-30 w-30 bg-green-800 p-4 mt-4" />
    </div>
    <h3 class="pt-4 opacity-90 text-center">DWH管理者A</h3>
    <h2 v-click class="py-2 text-center">AWSの遊び人</h2>
    <ul class="pt-6 h-30 opacity-80">
      <li>AWS コンソール シッテル</li>
      <li>コード カケナイ</li>
    </ul>
  </div>
  <div class="p-4">
    <div class="flex justify-center items-center">
      <mdi-account class="rounded-full h-30 w-30 bg-purple-800 p-4 mt-4" />
    </div>
    <h3 class="pt-4 opacity-90 text-center">DWH管理者B</h3>
    <h2 v-click class="py-2 text-center">ETLの賢者</h2>
    <ul class="pt-6 h-30 opacity-80">
      <li>レガシー ナラ マカセテ</li>
      <li>ダジャレ トクイ</li>
      <li v-after>ショウユウコト</li>
    </ul>
  </div>
  <div class="p-4">
    <img src="/profile.png" class="rounded-full h-30 w-30 mx-auto mt-4" />
    <h3 class="pt-4 opacity-90 text-center">WinterYukky</h3>
    <h2 v-click class="py-2 text-center">アプリの戦士</h2>
    <ul class="pt-6 h-30 opacity-80">
      <li>WEB アプリ チョットデキル</li>
      <li>コンテナ チョットデキル</li>
    </ul>
  </div>
</div>

<style>
li {
  font-size: 1.0rem !important;
}
</style>

<!-- 
そのプロジェクトはDWHを管理するチームでBIツールを作成したかったようですがDWHを管理するメンバーしかいなかったため、アプリ開発要員として私がアサインされました。
 -->

---
clicks: 7
class: text-dot
---

<v-rpg-panel class="grid grid-cols-3 text-center w-2/5 divide-y-2">
  <div class="py-2" style="border-top: 0">DWH管理者A</div>
  <div class="py-2" style="border-top: 0">DWH管理者B</div>
  <div class="py-2" style="border-top: 0">WinterYukky</div>
  <div class="py-2">
    <div><strong>Ｈ</strong>９９９</div>
    <div><strong>Ｍ</strong>　　０</div>
    <div><strong>あ</strong>：２６</div>
  </div>
  <div class="py-2">
    <div><strong>Ｈ</strong>　０３</div>
    <div><strong>Ｍ</strong>　０３</div>
    <div><strong>け</strong>：５８</div>
  </div>
  <div class="py-2">
    <div><strong>Ｈ</strong>１２４</div>
    <div><strong>Ｍ</strong>１２４</div>
    <div><strong>せ</strong>：２３</div>
  </div>
</v-rpg-panel>
<!-- エネミー -->
<div 
 :class="{ 'opacity-0': $slidev.nav.clicks >= 7 }" 
 class="h-1/2 grid items-center justify-center"
>
  <img src="/スライム.svg" class="filter blur-md h-30"/>
</div>
<!-- 戦闘開始コンソール -->
<v-rpg-panel v-if="$slidev.nav.clicks === 0" class="p-4 w-full h-2/7" style="cursor: pointer">
  <div>PoC開発タスクが　あらわれた！</div>
</v-rpg-panel>
<div v-if="$slidev.nav.clicks === 1" class="grid grid-cols-2 gap-2 h-2/7">
  <v-rpg-char-menu>
    <template #name>DWH管理者A</template>
  </v-rpg-char-menu>
  <v-rpg-panel class="flex justify-around py-2">
    <div>PoC開発タスク</div>
    <div>1件</div>
  </v-rpg-panel>
</div>
<v-rpg-panel v-if="$slidev.nav.clicks === 2" class="p-4 w-full h-2/7">
  <div>DWH管理者Aは　AWS環境を　構築した！</div>
</v-rpg-panel>
<div v-if="$slidev.nav.clicks === 3" class="grid grid-cols-2 gap-2 h-2/7">
  <v-rpg-char-menu>
    <template #name>DWH管理者B</template>
  </v-rpg-char-menu>
  <v-rpg-panel class="flex justify-around py-2">
    <div>PoC開発タスク</div>
    <div>1件</div>
  </v-rpg-panel>
</div>
<v-rpg-panel v-if="$slidev.nav.clicks === 4" class="p-4 w-full h-2/7">
  <div>DWH管理者Bを　ETLの仕組みを　構築した！</div>
</v-rpg-panel>
<div v-if="$slidev.nav.clicks === 5" class="grid grid-cols-2 gap-2 h-2/7">
  <v-rpg-char-menu>
    <template #name>WinterYukky</template>
  </v-rpg-char-menu>
  <v-rpg-panel class="flex justify-around py-2">
    <div>PoC開発タスク</div>
    <div>1件</div>
  </v-rpg-panel>
</div>
<v-rpg-panel v-if="$slidev.nav.clicks === 6" class="p-4 w-full h-2/7">
  <div>WinterYukkyは　アプリを　開発した！</div>
</v-rpg-panel>
<v-rpg-panel v-if="$slidev.nav.clicks === 7" class="p-4 w-full h-2/7">
  <div>PoC開発タスクを　完了した！</div>
</v-rpg-panel>

---
layout: center
class: text-center
---

# 無事、1か月でPoC開発を完了🎉
### <span v-click class="opacity-80">したのも束の間、プロト版に向けて追加の検証環境が必要に...</span>

---
clicks: 10
class: text-dot
---

<v-rpg-panel class="grid grid-cols-3 text-center w-2/5 divide-y-2">
  <div class="py-2" style="border-top: 0">DWH管理者A</div>
  <div class="py-2" style="border-top: 0">DWH管理者B</div>
  <div class="py-2" :class="{ 'text-red-500': $slidev.nav.clicks >= 8 }" style="border-top: 0">WinterYukky</div>
  <div class="py-2">
    <div><strong>Ｈ</strong>９９９</div>
    <div><strong>Ｍ</strong>　　０</div>
    <div><strong>あ</strong>：２６</div>
  </div>
  <div class="py-2">
    <div><strong>Ｈ</strong>　０３</div>
    <div><strong>Ｍ</strong>　０３</div>
    <div><strong>け</strong>：５８</div>
  </div>
  <div class="py-2" :class="{ 'text-red-500': $slidev.nav.clicks >= 8 }">
    <div><strong>Ｈ</strong>
      <template v-if="$slidev.nav.clicks <= 6">１２４</template>
      <template v-else-if="$slidev.nav.clicks <= 7">　６４</template>
      <template v-else>　　４</template>
    </div>
    <div><strong>Ｍ</strong>１２４</div>
    <div><strong>せ</strong>：２３</div>
  </div>
</v-rpg-panel>
<!-- エネミー -->
<div 
 v-if="$slidev.nav.clicks <= 6"
 class="h-1/2 grid items-center justify-center"
>
  <img src="/スライムベス.svg" class="filter blur-md h-30"/>
</div>
<div
  v-if="$slidev.nav.clicks === 7"
 class="h-1/2 grid items-center justify-center"
>
  <img v-motion-pop src="/スライムベス.svg" class="filter blur-md h-30" />
</div>
<div 
 v-if="$slidev.nav.clicks === 8"
 class="h-1/2 grid items-center justify-center"
>
  <img v-motion-pop src="/スライムベス.svg" class="filter blur-md h-30"/>
</div>
<div 
 v-if="$slidev.nav.clicks >= 9"
 :class="{ 'opacity-0': $slidev.nav.clicks >= 10 }" 
 class="h-1/2 grid items-center justify-center"
>
  <img v-motion-pop src="/スライムベス.svg" class="filter blur-md h-30"/>
</div>
<!-- 戦闘開始コンソール -->
<v-rpg-panel v-if="$slidev.nav.clicks === 0" class="p-4 w-full h-2/7">
  <div>環境追加タスクが　あらわれた！</div>
</v-rpg-panel>
<div v-if="$slidev.nav.clicks === 1" class="grid grid-cols-2 gap-2 h-2/7">
  <v-rpg-char-menu>
    <template #name>DWH管理者A</template>
  </v-rpg-char-menu>
  <v-rpg-panel class="flex justify-around py-2">
    <div>環境追加タスク</div>
    <div>1件</div>
  </v-rpg-panel>
</div>
<v-rpg-panel v-if="$slidev.nav.clicks === 2" class="p-4 w-full h-2/7">
  <div>DWH管理者Aは　DWHのメンテナンスを　している！</div>
</v-rpg-panel>
<div v-if="$slidev.nav.clicks === 3" class="grid grid-cols-2 gap-2 h-2/7">
  <v-rpg-char-menu>
    <template #name>DWH管理者B</template>
  </v-rpg-char-menu>
  <v-rpg-panel class="flex justify-around py-2">
    <div>環境追加タスク</div>
    <div>1件</div>
  </v-rpg-panel>
</div>
<v-rpg-panel v-if="$slidev.nav.clicks === 4" class="p-4 w-full h-2/7">
  <div>DWH管理者Bは　DWHのメンテナンスを　している！</div>
</v-rpg-panel>
<div v-if="$slidev.nav.clicks === 5" class="grid grid-cols-2 gap-2 h-2/7">
  <v-rpg-char-menu>
    <template #name>WinterYukky</template>
  </v-rpg-char-menu>
  <v-rpg-panel class="flex justify-around py-2">
    <div>環境追加タスク</div>
    <div>1件</div>
  </v-rpg-panel>
</div>
<v-rpg-panel v-if="$slidev.nav.clicks >= 6 && $slidev.nav.clicks <= 9" class="p-4 w-full h-2/7">
  <div class="my-1">WinterYukkyは　環境の追加を　試みた！</div>
  <div v-show="$slidev.nav.clicks >= 7" class="my-1 text-red-500">既存環境は　マネジメントコンソールで　作成されていた！</div>
  <div v-show="$slidev.nav.clicks >= 8" class="my-1 text-red-500">既存環境は　タグやネーミングルールも　設定されていなかった！</div>
  <div v-show="$slidev.nav.clicks >= 9" class="my-1 text-red-500">WinterYukkyは　命からがら　追加環境を構築した！</div>
</v-rpg-panel>
<v-rpg-panel v-if="$slidev.nav.clicks === 10" class="p-4 w-full h-2/7">
  <div>環境追加タスクを　完了した！</div>
</v-rpg-panel>

---
layout: center
class: text-center
---

<span class="opacity-80">構築はできたものの...</span>
# 後から環境の複製を作る難しさを痛感

---
layout: center
---

<h1>
  <span class="text-3xl opacity-60">そこで</span>
  <strong class="px-1">IaC</strong>
  <span class="text-3xl opacity-60">の導入を決定</span>
</h1>

---
layout: center
---

<h1>
  <span class="text-3xl opacity-60">最初は</span>
  <strong class="px-1">CloudFormation</strong>
  <span class="text-3xl opacity-60">を検討</span>
</h1>

---
layout: center
class: text-center
---

# が、少々ハードルが高かった
k8sの時も似たことを思いました

---

<h1>ハードルが高かった理由</h1>
<div class="grid grid-cols-5 items-center h-4/6 opacity-90">
  <ul class="col-span-3 bg-gray-800 rounded py-6 pl-4 mt-">
    <li>
      自身の能力不足
      <ul>
        <li>AWS全体の知識が少なかった</li>
        <li>Cfnは 『何から始めるべきか』 に時間がかかった</li>
      </ul>
    </li>
    <li>他メンバーは学習意欲が低い
      <ul>
        <li>学習コストを多めに見積もる必要があった</li>
        <li>自分だけなら学べば良いが、他人に強要はできない</li>
      </ul>
    </li>
  </ul>
  <div class="col-span-2 grid justify-center">
    <img src="/AWS-CloudFormation.svg" />
  </div>
</div>
<div v-click class="text-3xl mt-6"><mdi-arrow-right />これらを解決しないと、早い段階から結果を出すことは難しいと判断🤔</div>

<!-- 
自身の能力不足は学んでプロト開発までに間に合わせればいいですが、
他メンバーの学習意欲が低いという問題があり、それが対応できなければ運用時に問題になると考え
これらを解決することが必要だと判断しました
-->

---
layout: center
---

<h1>
  <span class="text-3xl opacity-60">そんな時に</span>
  <strong class="px-1">CDK</strong>
  <span class="text-3xl opacity-60">を知り、採用することに</span>
</h1>

<!-- 
CDKが先の課題を解決するのではと期待を込めて採用することにしました。
 -->

---
layout: center
---

<h1>
  <span class="text-3xl opacity-60">CDKを採用した</span>
  <strong>ポイント</strong>
</h1>

---
layout: center
---

# ① ドキュメントが<ruby>🐣<rp>(</rp><rt>初心者</rt><rp>)</rp></ruby>に優しいこと

---

# CloudFormationドキュメント
<div class="grid grid-cols-2">
  <div>
    <img src="/CloudFormation-API-Reference.png" />
  </div>
  <div class="grid items-center">
    <ul>
      <v-list-item icon="🥰" class="my-5">プロパティ毎に網羅的な説明</v-list-item>
      <v-list-item icon="😥" class="my-5">AWSのサービス知識が前提にある</v-list-item>
      <v-list-item icon="😇" class="my-5">例が長く初学者の壁になりやすい</v-list-item>
    </ul>
  </div>
</div>

---

# CDKはドキュメントが丁寧

<div class="grid grid-cols-2 items-center h-4/5">
  <div class="opacity-90">
    <ul>
      <v-list-item icon="👍" class="my-5"><strong>何がしたいか</strong>に対して簡潔な説明</v-list-item>
      <v-list-item icon="😭" class="my-5">サービス知識を前提としない</v-list-item>
      <v-list-item icon="🧩" class="my-5">組み合わせやすいサンプルコード</v-list-item>
    </ul>
  </div>
  <div>
    <img src="/CDK-API-Reference.png" />
  </div>
</div>

---

# ドキュメント量も豊富

<div class="grid grid-cols-2 items-center h-4/5">
  <div class="text-center text-2xl">
    ✨丁寧なドキュメントがこれだけ続く✨
  </div>
  <div class="grid justify-center h-full overflow-y-auto">
    <img src="/CDK-API-Reference-full.png" />
  </div>
</div>

---
layout: center
---

# ② 静的型チェックが効くこと

---

# CloudFormationの場合

<div class="grid grid-cols-5 items-center h-4/5">
  <div class="opacity-80 col-span-2">
    <h3>YAML or JSON構文チェック</h3>
    <v-x-o-list class="py-4">
      <li :class="{ 'x': $slidev.nav.clicks >= 1 }">
        許容されない値
        <div
          v-if="$slidev.nav.clicks >= 1"
          v-motion-pop
          class="pb-1 pl-10 text-xs opacity-60"
        >※ nodejs14<strong class="text-sm text-red-500">.x</strong>
        </div>
      </li>
      <li :class="{ 'x': $slidev.nav.clicks >= 2 }">
        存在しないプロパティ名
        <div 
          v-if="$slidev.nav.clicks >= 2"
          v-motion-pop
          class="pb-1 pl-10 text-xs opacity-60"
        >※ Han<strong class="text-sm text-red-500">d</strong>ler
        </div>
      </li>
      <li :class="{ 'x': $slidev.nav.clicks >= 3 }">
        誤ったデータ型
        <div 
          v-if="$slidev.nav.clicks >= 3"
          v-motion-pop
          class="pb-1 pl-10 text-xs opacity-60"
        >※ 128<strong class="pl-1 text-sm text-red-500 line-through">MB</strong>
        </div>
      </li>
      <li :class="{ 'x': $slidev.nav.clicks >= 4 }">
        誤った指定方法
        <div 
          v-if="$slidev.nav.clicks >= 4"
          v-motion-pop
          class="pb-1 pl-10 text-xs opacity-60"
        >※ <strong class="pl-1 text-red-500">arn:aws:iam::123456789012:role/</strong>lambda-role
        </div>
      </li>
    </v-x-o-list>
  </div>
  <div class="pl-6 col-span-3">

```yaml {all|6|9|10|11|all}
AWSTemplateFormatVersion: '2010-09-09'
Resources:
  Function1234:
    Type: AWS::Lambda::Function
    Properties:
      Runtime: nodejs14
      Code:
        ZipFile: 'exports.handler = ...'
      Hanbler: index.handler
      MemorySize: 128MB
      Role: lambda-role
```

  <div class="opacity-40 text-xs">※ このテンプレートの中に誤った記述がいくつかあります</div>
  </div>
</div>
<div v-click class="opacity-90">全ての間違いを見つけられましたか？</div>

---
layout: center
class: text-center
---

# CloudFormation <mdi-arrow-right /> L1 Construct
L1 Construct ･･･ CloudFormationから自動生成された型

---

# CDK L1 コンストラクトの場合

<div class="grid grid-cols-5 items-center h-4/5">
  <div class="opacity-80 col-span-2">
    <h3>TypeScript L1 型チェック</h3>
    <ul class="py-4">
      <v-list-item :icon="$slidev.nav.clicks >= 1 ? '❌' : '❓'">
        許容されない値
        <div
          v-if="$slidev.nav.clicks >= 1"
          v-motion-pop
          class="pb-1 pl-10 text-xs opacity-60"
        >※ string型では許容されない値を防げない
        </div>
      </v-list-item>
      <v-list-item :icon="$slidev.nav.clicks >= 2 ? '⭕' : '❓'">
        存在しないプロパティ名
        <div 
          v-if="$slidev.nav.clicks >= 2"
          v-motion-pop
          class="pb-1 pl-10 text-xs opacity-60"
        >※ 型に存在しないプロパティはエラーになる
        </div>
      </v-list-item>
      <v-list-item :icon="$slidev.nav.clicks >= 3 ? '⭕' : '❓'">
        誤ったデータ型
        <div 
          v-if="$slidev.nav.clicks >= 3"
          v-motion-pop
          class="pb-1 pl-10 text-xs opacity-60"
        >※ 型に合わない値はエラーになる
        </div>
      </v-list-item>
      <v-list-item :icon="$slidev.nav.clicks >= 4 ? '❌' : '❓'">
        誤った指定方法
        <div 
          v-if="$slidev.nav.clicks >= 4"
          v-motion-pop
          class="pb-1 pl-10 text-xs opacity-60"
        >※ string型では名前を入力されても防げない
        </div>
      </v-list-item>
    </ul>
  </div>
  <div class="pl-6 col-span-3">


```ts {all|3,11|5,15|6,16|7,17|all}
// L1 ContructのProps ※一部抜粋
interface CfnFunctionProps {
  runtime?: string;
  code: CodeProperty;
  handler?: string;
  memorySize?: number;
  role: string;
}

new lambda.CfnFunction(this, 'Function', {
  runtime: 'nodejs14',
  code: {
    zipFile: 'exports.handler = ...',
  },
  handler: 'index.handler',
  memorySize: 128,
  role: 'lambda-role', 
})
```

  </div>
</div>

---
layout: center
class: text-center
---

# L1 Construct <mdi-arrow-right /> L2 Construct
L2 Construct ･･･ L1 Constructを拡張した高度なモジュール

---

# CDK L2 コンストラクトの場合

<div class="grid grid-cols-5 items-center h-4/5">
  <div class="opacity-80 col-span-2">
    <h3>TypeScript L2 型チェック</h3>
    <ul class="py-4">
      <v-list-item :icon="$slidev.nav.clicks >= 1 ? '⭕' : '❓'">
        許容されない値
        <div
          v-if="$slidev.nav.clicks >= 1"
          v-motion-pop
          class="pb-1 pl-10 text-xs opacity-60"
        >※ Enumに定義されていない型を防げる
        </div>
      </v-list-item>
      <v-list-item :icon="$slidev.nav.clicks >= 2 ? '⭕' : '❓'">
        存在しないプロパティ名
        <div 
          v-if="$slidev.nav.clicks >= 2"
          v-motion-pop
          class="pb-1 pl-10 text-xs opacity-60"
        >※ 型に存在しないプロパティはエラーになる
        </div>
      </v-list-item>
      <v-list-item :icon="$slidev.nav.clicks >= 3 ? '⭕' : '❓'">
        誤ったデータ型
        <div 
          v-if="$slidev.nav.clicks >= 3"
          v-motion-pop
          class="pb-1 pl-10 text-xs opacity-60"
        >※ 型に合わない値はエラーになる
        </div>
      </v-list-item>
      <v-list-item :icon="$slidev.nav.clicks >= 4 ? '⭕' : '❓'">
        誤った指定方法
        <div 
          v-if="$slidev.nav.clicks >= 4"
          v-motion-pop
          class="pb-1 pl-10 text-xs opacity-60"
        >※ 指定されたインターフェース以外の型を防げる
        </div>
      </v-list-item>
    </ul>
  </div>
  <div class="pl-6 col-span-3">

```ts {all|3,12|5,14|6,15|7,10,16|all}
// L2 ContructのProps ※一部抜粋
interface FunctionProps {
  runtime: Runtime;
  code: Code;
  handler: string;
  memorySize?: number;
  role?: iam.IRole;
}

declare const myRole: iam.Role;
new lambda.Function(this, 'Function', {
  runtime: lambda.Runtime.NODEJS_14_X,
  code: lambda.Code.fromInline('inline code'),
  handler: 'index.handler',
  memorySize: 128,
  role: myRole,
})
```

  </div>
</div>

---
layout: center
---

# 型が初歩的なミスから守ってくれる🥰

---
layout: center
---

# ③ エディタのサポートがあること

---

# エディタのサポート

前項のタイプチェックに加え、例えば次のようなメリットを享受できる

<div class="grid grid-cols-2 items-center h-4/5">
  <div class="opacity-90">
    <ul>
      <li>マウスホバー等による型情報の取得</li>
      <li>型定義へのジャンプ</li>
      <li>色分けによる視覚的サポート</li>
      <li>カバレッジ表示</li>
      <li>その他様々なエディタ機能...</li>
    </ul>
  </div>
  <div>
    <img src="/CDKコーディング.webp" />
  </div>
</div>

---
layout: center
class: text-center
---

# これらが開発体験が良いと言われる理由の一部
故に始めやすかった

---
layout: quote
class: text-center
---

## 様々なサポートを受けられることで
# ✨初学者もIaCに入門しやすい✨
これがオススメする理由

---
title: これまでの運用における成功と失敗
---

<the-agenda :step="2" />

---
layout: section
---

# <strong class="text-rose-400">成功</strong><span class="opacity-70 text-4xl">したこと</span>

---
layout: center
class: text-center
---

# プロジェクトに関わるリソースを<br >可能な限りCDKで管理したこと

---
layout: center
class: text-center
---

<div>
  <div><strong class="text-green-400 text-4xl">Excel手順書</strong><span class="text-3xl opacity-90">プロジェクトと</span></div>
  <div><strong class="text-yellow-400 text-4xl">CDKを用いた</strong><span class="text-3xl opacity-90">プロジェクトで</span></div>
  <div class="text-3xl opacity-90">リリースコストを比較</div>
</div>

---

# <strong class="text-green-400">Excel手順書</strong>プロジェクト

<div class="grid grid-cols-2 items-center h-4/6 opacity-90">
  <div>
    <h3 class="pb-3">レビュー</h3>
    <ul>
      <v-list-item icon="📄">レビュー対象は手順書Excel</v-list-item>
      <v-list-item icon="🤔">レビュアーに判断基準を一任</v-list-item>
      <v-list-item icon="😥">レビューコスト高</v-list-item>
    </ul>
  </div>
  <div>
    <h3 class="pb-3">リリース作業</h3>
    <ul>
      <v-list-item icon="✋">手作業によるリリース</v-list-item>
      <v-list-item icon="🙄">作業者が作業を誤る可能性</v-list-item>
      <v-list-item icon="👻">履歴に残らない操作を生む可能性</v-list-item>
    </ul>
  </div>
</div>
<h2 v-click class="text-2xl"><mdi-arrow-right />リリース作業におけるメンバーの負荷が高かった</h2>

---

# CDKを導入したプロジェクト

<div class="grid grid-cols-2 items-center h-4/6 opacity-90">
  <div>
    <h3 class="pb-3">レビュー</h3>
    <ul>
      <v-list-item icon="📜">レビュー対象はソースコード</v-list-item>
      <v-list-item icon="🧪">テストや再現性のあるプレデプロイ</v-list-item>
      <v-list-item icon="😌">簡潔なコードでレビューコスト低</v-list-item>
    </ul>
  </div>
  <div>
    <h3 class="pb-3">リリース作業</h3>
    <ul>
      <v-list-item icon="🤖">自動化されたデプロイ</v-list-item>
      <v-list-item icon="🕶️">手作業を無くしてヒューマンミスを排除</v-list-item>
      <v-list-item icon="👣">過去の対応は全てGitの変更履歴に</v-list-item>
    </ul>
  </div>
</div>
<h2 v-click class="text-2xl"><mdi-arrow-right />プロダクトとメンバー両方を守ることに繋がった</h2>

---
layout: center
---

# メンバーのスキル習得ルートを具体化できたこと

---

<h1>そもそも、経験者の採用って難しい🤔</h1>
<div class="grid items-center h-4/6 opacity-90">
  <ul>
    <li>規模的にフロントエンドもバックエンドも対応できる人が必要</li>
    <li>TypeScript / Goの経験者がそもそも見つからない</li>
    <li>ビジネス上、いくらでもお金を出せるわけではない</li>
  </ul>
</div>
<h2 v-click class="text-2xl"><mdi-arrow-right />誰でもスキルアップできる環境作りが大事</h2>

---

<h1>スキルアップできる環境作り💪</h1>
<div class="grid items-center h-4/6 opacity-90">
  <ul>
    <li>TypeScript / Go / AWS・・・幅広い知識が必要🤔</li>
    <li>どういった順序で覚えてもらうといいのか🤔</li>
    <li>それぞれの知識を次の知識習得に活かせないか🤔</li>
  </ul>
</div>
<h2 v-click class="text-2xl"><mdi-arrow-right />複数言語で記述できるCDKが言語間のクッションに</h2>

---

# 段階的成長イメージ

<div class="grid grid-flow-col grid-cols-5 grid-rows-5 gap-x-2 h-4/5 px-12 text-center">
  <!-- アサイン時 -->
  <div class="grid row-span-3"></div>
  <div class="grid content-center rounded border border-dashed border-blue-500 text-sm"></div>
  <div class="grid content-center">
    アサイン時
    <div class="mt-2 opacity-0">
      <span class="rounded bg-blue-500 text-xs p-1"></span>
    </div>
  </div>
  <!-- フロントエンド開発 -->
  <div v-click class="grid row-span-3"></div>
  <div v-after class="grid content-center rounded-t bg-blue-500">TypeScript</div>
  <div v-after class="grid content-center">
    フロントエンド開発
    <div class="mt-2">
      <span class="rounded bg-blue-500 text-xs p-1">TypeScript学習</span>
    </div>
  </div>
  <!-- フロントエンドCDK -->
  <div v-click class="grid row-span-2"></div>
  <div v-after class="grid content-center rounded-t bg-yellow-600">CDK + TypeScript</div>
  <div v-after class="grid content-center bg-blue-500">TypeScript</div>
  <div v-after class="grid content-center">
    フロントエンドCDK
    <div class="mt-2">
      <span class="rounded bg-yellow-600 text-xs p-1">AWS学習</span>
    </div>
  </div>
  <!-- バックエンドCDK -->
  <div v-click class="grid"></div>
  <div v-after class="grid content-center rounded-t bg-teal-500">CDK + Go</div>
  <div v-after class="grid content-center bg-yellow-600">CDK + TypeScript</div>
  <div v-after class="grid content-center bg-blue-500">TypeScript</div>
  <div v-after class="grid content-center">
    バックエンドCDK
    <div class="mt-2">
      <span class="rounded bg-teal-500 text-xs p-1">Go学習</span>
    </div>
  </div>
  <!-- バックエンド開発 -->
  <div v-click class="grid content-center rounded-t bg-red-400">Go</div>
  <div v-after class="grid content-center bg-teal-500">CDK + Go</div>
  <div v-after class="grid content-center bg-yellow-600">CDK + TypeScript</div>
  <div v-after class="grid content-center bg-blue-500">TypeScript</div>
  <div v-after class="grid content-center">
    バックエンド開発
    <div class="mt-2 opacity-0">
      <span class="rounded bg-blue-500 text-xs p-1"></span>
    </div>
  </div>
</div>

<arrow v-click x1="180" y1="320" x2="650" y2="100" color="green" width="5" />

<div v-after class="text-2xl mt-4">
  <mdi-arrow-right /> メンバーのスキル習得ルートの具体化
</div>

<!-- 
こちらは段階的成長をイメージした図で
アサイン時、スキルを持っていない方だったとします。
まず、フロントエンド開発を経験していただきTypeScriptの知識を得ていただいています。
そこからそのフロントエンドのCDKをメンテナンスしていただきAWSとCDKの知識を得ていただきます。
次に、Goで記述されたバックエンドのCDKをメンテナンスしていただくことで、同様のインターフェースを実装しつつも言語間の特徴を捉えることでGo言語の習得を加速させます。
最後にGoのバックエンドアプリケーションもメンテナンスしていただく・・・といった形でメンバーのスキル習得ルートを具体化させました。
 -->

---
layout: section
---

# <strong class="text-sky-400">失敗</strong><span class="opacity-70 text-4xl">したこと</span>

---
layout: center
---

# 初期にスナップショットテストを入れていなかったこと

---

<h1>過去に唯一あった運用の失敗</h1>
<div class="grid grid-cols-2 gap-14 items-center h-4/6 opacity-90">
  <ul>
    <li>API Gateway V2を含むAPIプロジェクト</li>
    <li>
      デフォルトオーソライザーの実装が変更
      <ul>
        <li>認証要否が変わってAPIが全て失敗するように</li>
      </ul>
    </li>
    <li>CDKの単体テストでは検知できなかった</li>
    <li>E2Eテストで検知できたが、大きな教訓となった</li>
  </ul>
  <div>
    <img src="/ApiGatewayV2-fix-v1.108.0.png" />
  </div>
</div>
<h2 v-click class="text-2xl"><mdi-arrow-right />スナップショットテストは必ず入れよう📸</h2>

<style>
li {
  font-size: 1.2rem !important;
}
li li {
  font-size: 1rem !important;
}  
</style>

---

# v2.0.0以降における実験的モジュールの扱い
<div class="grid grid-cols-2 gap-14 h-4/6">
  <div class="border rounded p-3 m-3">
    <h3>v1</h3>
    <div class="text-xl my-2">安定モジュールと実験的モジュールが混在</div>
    <div class="border border-purple-400 rounded p-3">
      <div class="pb-4">@aws-cdk</div>
      <div class="bg-blue-500 rounded p-3"><mdi-check-bold class="text-green-400" />安定モジュール</div>
      <div class="bg-red-500 rounded p-3"><mdi-alert class="text-yellow-500" />実験的モジュール</div>
    </div>
  </div>
  <div class="border rounded p-3 m-3">
    <h3>v2</h3>
    <div class="text-xl my-2">安定モジュールと実験的モジュールが分離</div>
    <div class="border border-blue-500 rounded p-3">
      <div class="pb-4">aws-cdk-lib</div>
      <div class="bg-blue-500 rounded p-3"><mdi-check-bold class="text-green-400" />安定モジュール</div>
    </div>
    <div class="border border-red-500 rounded p-3 mt-4">
      <div class="pb-4">@aws-cdk/aws-xxx-alpha</div>
      <div class="bg-red-500 rounded p-3"><mdi-alert class="text-yellow-500" />実験的モジュール</div>
    </div>
  </div>
</div>

<arrow x1="400" y1="270" x2="550" y2="270" color="green" width="5" />
<arrow x1="400" y1="300" x2="550" y2="380" color="green" width="5" />

<div v-click class="text-xl mt-12">
  <mdi-arrow-right /> v2では、開発者が意図せず実験的モジュールを使う可能性がなくなった
</div>
<div v-click class="text-xl mt-2">
  <mdi-arrow-right /> それでも、スナップショットテストは入れよう😇
</div>

<!-- 
こちらは私の資料の中で唯一CDK V2について触れる部分です。
先ほどの問題になったAPI GatewayV2は実験的モジュールでした。この実験的モジュールの扱いはV2で変わっています。
具体的には、V1では安定モジュールと実験的モジュールが@aws-cdkパッケージに混在していましたが、V2ではこれが分離しています。安定モジュールはaws-cdk-libパッケージ、実験的モジュールは末尾にalphaと名の付くパッケージに分けられたことで開発者が意図せず実験的モジュールを使用する可能性がなくなりました。
 -->

---

<the-agenda :step="3" />

---

# Q. RUMのようにL2コンストラクト開発は必須ですか？

<div v-click class="grid items-center h-4/5">
  <div class="text-center">
    <h2>A. 構成次第ですが、よくある構成だと必要ないかも</h2>
    <div class="opacity-60 text-sm mt-4">初期のL2実装は多くありませんでしたが、今はかなり揃っています</div>
  </div>
</div>

---

# Q. どんな粒度でスタック分割していますか？

<div v-click class="grid items-center h-4/5">
  <div class="text-center">
    <h2>A. 基本的に分割していません</h2>
    <div class="opacity-60 text-sm mt-4">
      リソース数が多い、RDS等は別管理したいといった理由がある時だけ分割しています
    </div>
  </div>
</div>

---

# Q. CI/CDはどんな構成ですか？

<div v-click class="grid items-center h-4/5">
  <div class="text-center">
    <h2>A. GitLab CIを使用しています</h2>
    <div class="opacity-60 text-sm mt-4">
      次のスライドでポイントを説明します
    </div>
  </div>
</div>

---


# GitLab Runnerをセルフホスティング

<div class="grid grid-cols-2 items-center h-4/5">
  <div class="-mt-8">
    <ul class="opacity-80">
      <v-list-item icon="🏗️">AWS上に構築（これもCDK管理）</v-list-item>
      <v-list-item icon="🤖">常設しているのは管理用Runnerのみ</v-list-item>
      <v-list-item icon="📈">Runnerは0台~X台でスケール</v-list-item>
      <v-list-item icon="🏷️">RunnerをIAMロール毎にタグ付け</v-list-item>
    </ul>
    <div v-click class="mt-8 text-3xl">
      <mdi-arrow-right />
      <ruby>💰<rp>(</rp><rt>コスト</rt><rp>)</rp></ruby>
      と
      <ruby>🔑<rp>(</rp><rt>権限</rt><rp>)</rp></ruby>
      を最適化
    </div>
  </div>
  <div class="h-full mx-auto">
    <img src="/GitLabRunner構成.svg" class="h-4/5" />
  </div>
</div>

---

# デプロイのポイント

<div class="grid grid-cols-2 gap-4 items-center h-4/5">
  <div class="h-full">
    <div class="opacity-60">.gitlab-ci.yml</div>

```yaml
deploy_production:
  stage: deploy
  variables:
    APP_ENV: production
    APP_DOMAIN: example.com
  only:
    - tags
```

<div class="mt-4 opacity-60">bin/cdk-app.ts</div>

```ts
const env = process.env.APP_ENV
const domain = process.env.APP_DOMAIN
const app = new cdk.App()
new ExampleStack(app, `${env}-ExampleStack`, {
  env,
  domain
}
```

  </div>
  <div class="-mt-8">
    <ul class="opacity-90">
      <li>
        タグ付けトリガー
        <ul>
          <li>複雑なブランチ管理を排除</li>
          <li>リリースノートによる参照性</li>
          <li>保護タグ機能で権限管理</li>
        </ul>
      </li>
      <li class="mt-4">
        環境毎の差は環境変数で注入
        <ul>
          <li>
            環境値をスタック名に利用して重複回避
            <ul>
              <v-list-item icon="※" class="text-sm">シングルアカウントの場合</v-list-item>
            </ul>
          </li>
          <li>
            スタック内で直接参照せず<span class="text-yellow-400">Props</span>を用いる
            <ul>
              <v-list-item icon="※" class="text-sm">ここが重要</v-list-item>
            </ul>
          </li>
        </ul>
      </li>
    </ul>
  </div>
</div>

<style>
li li li {
    font-size: 1rem !important;
}
</style>

---

# Review Apps

<div class="grid grid-cols-2 items-center h-4/5">
  <div>
    <ul class="opacity-90">
      <li>
        変更内容の事前検証
        <ul>
          <li>MR毎に環境をデプロイ</li>
          <li>CDK(Cfn)の弱点をカバー</li>
        </ul>
      </li>
      <li>
        時間制限を設定
        <ul>
          <li>auto_stop_inで指定（例：1 hour）</li>
          <li>時間課金のコストをカット</li>
        </ul>
      </li>
      <li>自動化できない部分のテストに重宝</li>
    </ul>
  </div>
  <div class="mx-auto">
    <img src="/GitLab-Review-Apps.png" />
  </div>
</div>

---
layout: center
---

# CI/CDの知識を持つメンバーがいない・・・😔

---
layout: center
---

# そんな時にはCDK パイプライン

---

# CDK パイプライン

<div class="grid grid-cols-2 items-center h-4/5">
  <div>
    <ul class="opacity-90">
      <li v-click>CodePipelineの高度なコンストラクト</li>
      <li v-click>CDKアプリをデプロイすることに特化</li>
      <li v-click>自身を動かすパイプラインを定義</li>
      <li v-click>マルチアカウントも楽々</li>
    </ul>
  </div>
  <div>
    <div class="opacity-60">マルチアカウントの例</div>

```ts
declare const pipeline: pipelines.CodePipeline

// Staging
const stg = new AppStage(this, 'Staging', {
  env: { account: '11111', region: 'us-east-1' },
})
pipeline.addStage(stg)

// Production with manual approval
const prod = new AppStage(this, 'Production', {
  env: { account: '99999', region: 'us-east-1' },
})
pipeline.addStage(prod)
```

  </div>
</div>

---
layout: section
---

# さいごに

---

# ここまで実現できたこと

<div class="grid grid-cols-2 h-4/5 items-center">
  <ul class="opacity-90">
    <v-list-item v-click icon="✅">初心者でも素早くIaCを導入</v-list-item>
    <v-list-item v-click icon="✅">AWSの世界に楽しく入門</v-list-item>
    <v-list-item v-click icon="✅">3年目になっても苦にならない運用</v-list-item>
    <v-list-item v-click icon="✅">新しいAWSサービスのスムーズな導入</v-list-item>
  </ul>
  <div>
    <div v-click class="text-center">
      <span class="opacity-90 text-3xl">これら全て</span><strong class="text-yellow-400 text-5xl">CDK</strong><span class="opacity-90 text-3xl">のおかげ</span>
    </div>
  </div>
</div>

---
layout: center
class: text-center
---

<h1>
  <strong class="text-rose-400 text-5xl">AWS</strong>
  <span class="opacity-80">も</span><strong class="text-sky-400 text-5xl">IaC</strong>
  <span class="opacity-80">も始めたい</span>方<br>
  <strong class="text-yellow-400 text-5xl">CDK</strong><span class="opacity-80">からスタートしてみてはいかがでしょうか</span>😌
</h1>

---
layout: center
---

# 🥰Thanks🥰