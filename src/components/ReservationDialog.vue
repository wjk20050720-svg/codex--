<script setup>
import { computed, ref, watch } from 'vue'
const props = defineProps({ open: Boolean })
const emit = defineEmits(['close'])
const succeeded = ref(false)
const date = ref('')
const minDate = computed(() => {
  const today = new Date()
  return new Date(today.getTime() - today.getTimezoneOffset() * 60000).toISOString().slice(0, 10)
})
const dialog = ref(null)
watch(() => props.open, (open) => {
  if (open) {
    succeeded.value = false
    if (!dialog.value?.open) dialog.value?.showModal()
  } else if (dialog.value?.open) dialog.value.close()
})
function close() { emit('close') }
function submit() { succeeded.value = true }
</script>

<template>
  <dialog ref="dialog" class="booking-dialog" @click.self="close" @close="close">
    <button class="dialog-close" aria-label="关闭" @click="close">×</button>
    <template v-if="!succeeded">
      <p class="eyebrow"><i></i> RESERVE A TABLE</p><h2>预订一席</h2><p class="dialog-intro">告诉我们你的到店计划，我们会尽快与您确认。</p>
      <form class="booking-form" @submit.prevent="submit">
        <label>称呼<input name="name" required placeholder="怎么称呼您" /></label>
        <label>联系电话<input name="phone" type="tel" required pattern="[0-9+\- ]{6,}" placeholder="请输入手机号码" /></label>
        <div class="form-row"><label>到店日期<input v-model="date" name="date" type="date" :min="minDate" required /></label><label>用餐人数<select name="guests"><option>2 位</option><option>1 位</option><option>3 位</option><option>4 位</option><option>5 位及以上</option></select></label></div>
        <button class="booking-submit" type="submit">提交预约 <span>↗</span></button><p class="form-note">提交后我们将致电确认席位</p>
      </form>
    </template>
    <div v-else class="booking-success"><span>✓</span><h3>收到你的预约意向</h3><p>山隐会尽快与您联系确认，期待相见。</p></div>
  </dialog>
</template>
