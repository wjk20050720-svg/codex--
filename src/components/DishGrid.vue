<script setup>
defineProps({ category: { type: String, required: true } })
const items = [
  { type: 'season', image: 'photo-1547592180-85f173990554', alt: '春笋炖溪鱼', tag: '当令鲜味', name: '春笋炖溪鱼', description: '山泉慢煨 · 笋香清甜', price: '168' },
  { type: 'signature', image: 'photo-1504674900247-0877df9cc836', alt: '炭火慢烤和牛', tag: '山隐招牌', name: '炭火慢烤和牛', description: '山胡椒 · 野蜂蜜汁', price: '238' },
  { type: 'season', image: 'photo-1512621776951-a57141f2eefd', alt: '山野春蔬', tag: '当令鲜味', name: '山野春蔬', description: '时令野菜 · 青梅醋汁', price: '20' },
  { type: 'signature', image: 'photo-1476224203421-9ac39bcb3327', alt: '石锅菌菇饭', tag: '山隐招牌', name: '石锅菌菇饭', description: '野生菌菇 · 山泉米', price: '98' },
  { type: 'season', image: 'photo-1546069901-ba9599a7e63c', alt: '桂花酒酿圆子', tag: '时令甜品', name: '桂花酒酿圆子', description: '手酿酒酿 · 糖桂花', price: '48' },
  { type: 'signature', image: 'photo-1490645935967-10de6ba17061', alt: '山野风味拼盘', tag: '山隐招牌', name: '山野风味拼盘', description: '腌笃鲜 · 山胡桃 · 青梅', price: '128' },
]
</script>

<template>
  <div class="dish-grid">
    <article v-for="(dish, index) in items" v-show="category === 'all' || dish.type === category" :key="dish.name" class="dish-card">
      <div class="dish-photo"><img :src="`https://images.unsplash.com/${dish.image}?auto=format&fit=crop&w=900&q=85`" :alt="dish.alt" loading="lazy" /><span class="dish-tag">{{ dish.tag }}</span><span class="dish-number">{{ String(index + 1).padStart(2, '0') }}</span></div>
      <div class="dish-info"><div><h3>{{ dish.name }}</h3><p>{{ dish.description }}</p></div><span class="dish-price">¥ {{ dish.price }}</span></div>
    </article>
  </div>
</template>
