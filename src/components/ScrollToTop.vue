<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import { Button } from '@/components/ui/button';
import { ArrowUp } from 'lucide-vue-next';

const isVisible = ref(false);

const handleScroll = () => {
  if (window.scrollY > 300) {
    isVisible.value = true;
  } else {
    isVisible.value = false;
  }
};

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth',
  });
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<template>
  <div
    v-if="isVisible"
    class="fixed bottom-8 right-8 z-50"
  >
    <Button
      @click="scrollToTop"
      class="rounded-full h-12 w-12"
      size="icon"
      aria-label="Scroll to top"
    >
      <ArrowUp class="h-6 w-6" />
    </Button>
  </div>
</template> 