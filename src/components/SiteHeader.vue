<script setup>
defineProps({ menuOpen: Boolean })
defineEmits(['toggle-menu', 'book', 'close-menu'])
</script>

<template>
  <header class="site-header">
    <a class="brand" href="#home" aria-label="山隐首页"><span class="brand-mark">山</span><span class="brand-name">山隐 <small>SHAN YIN</small></span></a>
    <button class="menu-toggle" aria-label="打开菜单" :aria-expanded="menuOpen" @click="$emit('toggle-menu')"><span></span><span></span></button>
    <nav class="main-nav" :class="{ open: menuOpen }" aria-label="主导航">
      <a class="active" href="#home" @click="$emit('close-menu')">首页</a><a href="#story" @click="$emit('close-menu')">关于山隐</a><a href="#menu" @click="$emit('close-menu')">时令菜单</a><a href="#visit" @click="$emit('close-menu')">寻访我们</a>
      <button class="nav-booking" @click="$emit('book')">预约席位 <span>↗</span></button>
    </nav>
  </header>
</template>
