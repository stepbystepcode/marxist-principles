<template>
  <q-page>
    <div class="row q-ma-lg q-pt-xl">
      <q-carousel style="flex:1;height:auto;aspect-ratio: 16/9;" animated v-model="slide" navigation infinite
                  :autoplay="autoplay" arrows transition-prev="slide-right" transition-next="slide-left"
                  @mouseenter="autoplay = false" @mouseleave="autoplay = true">
        <q-carousel-slide :name="1" img-src="/banner/1.jpg"/>
        <q-carousel-slide :name="2" img-src="/banner/2.jpg"/>
        <q-carousel-slide :name="3" img-src="/banner/3.jpg"/>
        <q-carousel-slide :name="4" img-src="/banner/4.jpg"/>
      </q-carousel>
      <div style="flex:1" class="q-px-lg">
        <q-list bordered separator>
          <q-item>
            <q-item-section>
              精选文章:
            </q-item-section>
          </q-item>

          <q-item v-for="doc in docs" :key="doc" clickable v-ripple>
            <q-item-section>
              <q-item-label @click="go(doc.title)">{{ doc.title }}</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </div>
    </div>
    <div class="row q-pt-md q-mb-xl flex-center">
      <div v-for="(p,i) in person" :key="i" class="column">
        <a style="text-decoration: none;color: black" :href="`https://www.hudong.com/wikiid/${p.id}`" target="_blank">
          <img :src="`/person/${i}.jpg`" alt="" class="q-gutter-md-x-sm">
          <div class="text-h6 text-center">{{ p.name }}</div>
        </a>
      </div>
      <p class="q-pa-xl text-h6 bg-yellow-2 q-mt-md">
        马克思主义是一种理论，也是一项事业。通过唯物史观和辩证法，马克思主义者可以深刻剖析阶级斗争、研究建立在经济基础上的社会关系以及资本主义主导下的社会形态，进而积极地参与改变世界。
        工人运动和共产主义运动史留下了大量珍贵文献，需要我们收集、学习。这正是马克思主义文库的工作重心。</p>
    </div>
    <div class="column q-py-md bg flex-center">
      <h5 style="font-family: 'Noto Serif SC', serif;">学术著作</h5>
      <div class="flex-center row q-mx-xl q-gutter-lg">
        <div v-for="i in 10" :key="i" class="book column">
          <img :src="`/books/${i}.jpg`" alt="">
        </div>
      </div>
    </div>
    <div class="column q-py-md flex-center">
    <h5>人物百科</h5>
    <div class="row">
      <ul v-for="list in lists" :key="list">
        <li v-for="a in list" :key="a"><a :href="`https://baike.baidu.com/item/${a}`" target="_blank">{{ a }}</a></li>
      </ul>
    </div>
      <h5>书籍📚下载</h5>
      <div class="row q-gutter-md">
        <div v-for="book in books" :key="book" >
              <a :href="`/files/${book.file}`" :download="`${book.name}.epub`" class="column text-center" >
          <img :src="book.img" alt="book.name" style="width: 200px;height: 300px">
          {{book.name}}</a></div>
      </div>
    <h5>学习思维导图</h5>
    <q-img src="/files/map.png"></q-img>
    </div>
  </q-page>
</template>

<script setup>
import {ref} from 'vue'
import {useRouter} from 'vue-router'

const router = useRouter();
const slide = ref(1);
const autoplay = ref(true);
const docs = [
  {title: '自然辩证法', file: '自然辩证法.pdf'},
  {title: '政治经济学', file: '政治经济学.pdf'},
  {title: '哲学的贫困', file: '哲学的贫困.pdf'}
]
const books = [
  {name:'马克思恩格斯全集',file:'1.epub',img:'/books/down-1.jpg'},
  {name:'列宁全集',file:'2.epub',img: '/books/down-2.jpg'},
  {name:'马克思主义思想字典',file:'marxistthought.pdf',img: '/books/down-3.jpg'},
]
const lists = [
  ['李大钊', '邓中夏', '彭述之', '陈碧兰', '郑超麟', '王凡西', '楼国华', '陈其昌', '尹宽', '王独清', '刘仁静', '蔡振德', '李季'],
  ['毛泽东', '林彪', '周恩来', '刘少奇', '恽代英', '罗亦农', '瞿秋白', '罗章龙', '向警予', '蔡和森', '赵世炎', '张国焘', '王明', '江亢虎', '李立三'],
  ['周仁生', '姜君羊', '刘平梅', '谢山', '熊安东', '赵芳举'],
  ['蒲鲁东', '巴枯宁', '克鲁泡特金', '马赫诺', '爱玛·戈德曼', '刘师复', '巴金', '大卫·格雷伯'],
  ['布朗基', '拉法格', '饶勒斯', '拉萨尔', '威廉·李卜克内西', '倍倍尔', '卡尔·李卜克内西', '梅林', '考茨基', '伯恩斯坦', '奥托·鲍威尔', '帕尔乌斯'],
  ['普列汉诺夫', '巴布石金', '柯伦泰', '克鲁普斯卡娅', '布哈林', '普列奥布拉任斯基', '阿克雪里罗得', '卢那察尔斯基', '施略普尼科夫', '季诺维也夫', '加米涅夫', '波格丹诺夫', '梁赞诺夫', '沃兹涅先斯基', '伏龙芝', '斯大林'],
  ['拉狄克', '葛兰西', '卢卡奇', '蔡特金', '保尔·列维', '潘涅库克', '科尔施', '库恩·贝拉', '台尔曼', '罗易', '马林', '约翰·里德', '马里亚特吉', '幸德秋水', '片山潜', '安德烈乌·宁', '毛林', '霍查', '铁托'],
  ['坎农', '弗朗克', '韩生', '迈坦', '诺瓦克', '曼德尔', '多伊彻', '伊罗生', '李福仁', '勃鲁埃', '罗高文', '本赛德', '克里斯·哈曼', '克里夫', '泰德·格兰特', '罗斯多尔斯基', '多布', '格瓦拉', '卡斯特罗'],
  ['福斯特', '斯威齐', '弗洛姆', '本雅明', '布雷弗曼', '拉斯基', '密利本德', '霍布斯鲍姆', '汤普森', '威廉斯', '艾伦·伍德', '埃里克·赖特', '萨米尔·阿明', '杜波依斯'],
  ['杜娜叶夫斯卡娅', '萨特', '阿多诺', '马尔库塞', '阿尔都塞', '爱德华·卡德尔', '米·马尔科维奇', '弗兰尼茨基', '亚当·沙夫', '加约·彼得洛维奇', '贝尔·胡克斯']
];

const person = ref(['', {
  name: '马克思',
  id: '1694885037647269041'
}, {
  name: '恩格斯',
  id: '5054480029629308815'
}, {name: '列宁', id: '2723928339007466935'}, {name: '罗莎·卢森堡', id: '827906437945979792'}, {
  name: '托洛茨基',
  id: '2202207472452673899'
}, {name: '陈独秀', id: '9170172356796784893'}]);
const go = (url)=>{
  // window.open(url,"_blank");
  router.push(`/book/${url}`);
}
</script>
<style scoped lang="scss">
.bg {
  background-color: #d6d6d6b0;
}

.book {
  img {
    width: 7rem;
    aspect-ratio: 9/14;
    border: 1px solid black;
    box-shadow: 6px 9px 4px rgba(0, 0, 0, 0.24);
    transition: All 0.4s ease-in-out;
    margin-top: 0;

    &:hover {
      transform: translate(0, -10px);

    }
  }
}
</style>
