<template>
  <span ref="rootEl">{{ formattedValue }}</span>
</template>

<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted } from 'vue'

interface Props {
  endValue: number
  duration?: number
  suffix?: string
  prefix?: string
  decimals?: number
}

const props = withDefaults(defineProps<Props>(), {
  duration: 2200,
  suffix: '',
  prefix: '',
  decimals: 0
})

const current = ref(0)
const hasAnimated = ref(false)
const rootEl = ref<HTMLElement | null>(null)

const formattedValue = computed(() => {
  const factor = Math.pow(10, props.decimals)
  const value =
    props.decimals > 0
      ? Math.round(current.value * factor) / factor
      : Math.round(current.value)

  return `${props.prefix}${value.toLocaleString('ru-RU')}${props.suffix}`
})

const animate = () => {
  if (hasAnimated.value) return
  hasAnimated.value = true

  const start = 0
  const end = props.endValue
  const duration = props.duration
  const startTime = performance.now()

  const easeOutCubic = (t: number) => 1 - Math.pow(1 - t, 3)

  const step = (now: number) => {
    const elapsed = now - startTime
    const progress = Math.min(elapsed / duration, 1)
    const eased = easeOutCubic(progress)

    current.value = start + (end - start) * eased

    if (progress < 1) {
      requestAnimationFrame(step)
    } else {
      current.value = end
    }
  }

  requestAnimationFrame(step)
}

let observer: IntersectionObserver | null = null

onMounted(() => {
  if (!process.client || !rootEl.value) return

  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          animate()
          observer?.disconnect()
        }
      })
    },
    {
      threshold: 0.3
    }
  )

  observer.observe(rootEl.value)
})

onUnmounted(() => {
  if (observer && rootEl.value) {
    observer.unobserve(rootEl.value)
    observer.disconnect()
  }
})
</script>

<style scoped>
span {
  display: inline-block;
}
</style>


