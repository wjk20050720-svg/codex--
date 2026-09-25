<script setup>
import { ref } from 'vue'
import SiteHeader from './components/SiteHeader.vue'
import HeroSection from './components/HeroSection.vue'
import DishGrid from './components/DishGrid.vue'
import ReservationDialog from './components/ReservationDialog.vue'

const menuOpen = ref(false)
const category = ref('all')
const bookingOpen = ref(false)
const categories = [
  { id: 'all', name: '全部', count: '06' },
  { id: 'season', name: '时令推荐', count: '03' },
  { id: 'signature', name: '山隐招牌', count: '03' },
]
</script>

<template>
  <SiteHeader :menu-open="menuOpen" @toggle-menu="menuOpen = !menuOpen" @close-menu="menuOpen = false" @book="bookingOpen = true" />
  <main>
    <HeroSection />
    <section class="intro section-pad" id="story">
      <div class="section-label"><span>01 / OUR PHILOSOPHY</span><span>山隐之道</span></div>
      <div class="intro-grid"><div class="intro-title"><p class="eyebrow"><i></i> FROM NATURE TO TABLE</p><h2>顺应时节，<br />不时不食。</h2></div><div class="intro-text"><p>每一季都有值得期待的味道。我们认真挑选当季食材，用熟悉又用心的烹调，为你和重要的人准备一桌热气腾腾的好菜。愿每次相聚，都能在这里吃得舒服、聊得尽兴。</p><a class="text-link" href="#visit">认识山隐 <span>↗</span></a></div></div>
      <div class="intro-photo"><img src="https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?auto=format&fit=crop&w=1800&q=85" alt="温暖安静的餐厅空间" loading="lazy" /><div class="photo-caption">一方山居，容纳四时风物 <span>EST. 2018</span></div></div>
    </section>
    <section class="menu-section section-pad" id="menu">
      <div class="section-label"><span>02 / SEASONAL MENU</span><span>时令风物</span></div>
      <div class="menu-heading"><div><p class="eyebrow"><i></i> TASTE THE SEASON</p><h2>此时，此味。</h2></div><p>春笋、溪鱼、山野菌菇……<br />从一方山野，拾得一席鲜味。</p></div>
      <div class="menu-tabs" role="tablist" aria-label="菜单分类"><button v-for="item in categories" :key="item.id" :class="{ selected: category === item.id }" :aria-selected="category === item.id" role="tab" @click="category = item.id">{{ item.name }} <span>{{ item.count }}</span></button></div>
      <DishGrid :category="category" />
      <a class="all-menu" href="#visit">查看完整菜单 <span>↗</span></a>
    </section>
    <section class="quote-band"><div class="quote-inner"><span class="quote-mark">“</span><blockquote>让食物回到土地，<br />让味道记住季节。</blockquote><p>山隐 · 用一餐的时间，亲近自然</p></div><div class="quote-side">GOOD FOOD<br />GROWS HERE</div></section>
    <section class="visit-section section-pad" id="visit">
      <div class="section-label"><span>03 / COME FIND US</span><span>山中有席</span></div>
      <div class="visit-grid"><div class="visit-copy"><p class="eyebrow"><i></i> A PLACE TO SLOW DOWN</p><h2>城市一隅，<br />好味值得。</h2><p class="visit-description">在上海留一张桌子给你。<br />于日常街巷中，慢下来尝一席山野时令。</p><div class="visit-details"><div><span>地址</span><p>上海市长宁区（具体门店地址待补充）</p></div><div><span>营业时间</span><p>周一至周日&nbsp; 11:30—14:00 / 17:30—21:30</p></div></div><button class="booking-button" @click="bookingOpen = true">预订一席 <span>↗</span></button></div><div class="visit-image"><img src="https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?auto=format&fit=crop&w=1200&q=85" alt="山隐餐厅的用餐空间" loading="lazy" /><div class="open-badge"><span>OPEN</span><b>11:30</b><small>EVERY DAY</small></div></div></div>
    </section>
  </main>
  <footer class="site-footer"><a class="brand footer-brand" href="#home"><span class="brand-mark">山</span><span class="brand-name">山隐 <small>SHAN YIN</small></span></a><p>循山而食，顺时而味。</p><div class="footer-bottom"><span>© 2025 SHAN YIN RESTAURANT</span><span>上海</span><a href="#home">回到顶部 ↑</a></div></footer>
  <ReservationDialog :open="bookingOpen" @close="bookingOpen = false" />
</template>
